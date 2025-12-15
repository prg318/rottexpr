# prg/rottexpr fork details
This repository contains a fork of [Steven LeVesque's fork](https://github.com/LTCHIPS/rottexpr) of the [icculus.org Rise of the Triad Linux port](https://icculus.org/rott/). This fork adds some additional options as well as macOS and Windows/msys2 build support. Some of the new options include:

- SCALE2X
- SCALE3X
- SCALE4X
- NOSOUND

Pull requests, issues, and suggestions are welcome.

## Build Instructions

`rottexpr` can be built for Windows, Linux, and macOS.
In order to build, you'll need to install the SDL2 and SDL2_mixer libraries.

On MSYS2 MINGW64:

    pacboy -S SDL2:x SDL2_mixer:x

On macOS:

    brew install sdl2 sdl2_mixer

On Debian:

    apt install libsdl2-dev libsdl2-mixer-dev

On Arch Linux:

    pacman -S sdl2 sdl2_mixer

On FreeBSD:

    pkg install sdl2 sdl2_mixer gmake   # Remember to run `gmake` instead of BSD's `make`

Once you have the dependencies installed, run the following command in the project root:

    make -C src

This will build the `rott` or `rott.exe` binary in the `src` directory.
In order to run, change directory to your game installation (the base directory with `DARKWAR.WAD`) and run `rott`.

## Music

On Windows, music should work out of the box because Windows includes a very nice soundfont with your Windows install.
On Linux and macOS, you will need to provide a soundfont in order for SDL2 to play the MIDI files.
First, you'll need to acquire an SF2-format soundfont. There's a wide variety of soundfonts that you can use with SDL2, but if you don't have one you can use the Fluid soundfont.  Here's a [direct link to the fluid soundfont zip from Debian's mirrors](http://deb.debian.org/debian/pool/main/f/fluid-soundfont/fluid-soundfont_3.1.orig.tar.gz).
You'll need to set the `SDL_SOUNDFONTS` environment variable and point it at the soundfont you'd like to use:

    export SDL_SOUNDFONTS=/usr/share/soundfonts/FluidR3_GM.sf2

With the `SDL_SOUNDFONTS` environment variable properly pointing at a valid SF2 soundfont, SDL2_mixer should be able to playback the MIDI files. This is well worth your time because the Rise of the Triad soundtrack is absolutely incredible - shout out to [Lee Jackson - an absolute legend](https://dleejackson.lbjackson.com/).

## Known Issues

- Builds successfully on FreeBSD, but fails to start

# rottexpr - Original README

Based off of the icculus Rise of the Triad source port
(can be found here: https://icculus.org/rott/)

This source port of Rise of the Triad features the following:

Now runs off of SDL2!  
Support for resolutions from 320x200 all the way to 3840x2160  
Adaptive HUD positioning (no more status bar being off to the side)  
HUD scaling (HUD scaling for bottomless HUD coming later)  
Support for bordered and borderless windowed modes

New gameplay options:

* Blitzguards being outfitted with any weapon from the missile/magic weapon
  arsenal! Yes, that means Blitzguards can use excalibats too!
* You can now pick up ammo from dropped missile weapons!
* A special respawning enemy game mode called ZomROTT, where you have to gib
  your enemies to keep them from coming back!
* Toggleable Auto Aim
* Auto Aim for Missile Weapons
* ...and more

And all of the improvements made in the icculus source port...

To run the game you'll need the following things:

`SDL2.dll` (https://www.libsdl.org/download-2.0.php)

`SDL2_mixer.dll` (https://www.libsdl.org/projects/SDL_mixer/)

And the files:

```
DEMO1_3.DMO
DEMO2_3.DMO
DEMO3_3.DMO
DEMO4_3.DMO
REMOTE1.RTS
```

And

```
DARKWAR.RTC
DARKWAR.RTL
DARKWAR.WAD
```

Or

```
HUNTBGIN.RTC
HUNTBGIN.RTL
HUNTBGIN.WAD
```

Place all those files in the same directory as `rott.exe`.


BUILDING:

To build the project, you'll need the SDL2.0 development libraries
(https://www.libsdl.org/download-2.0.php) as well as the SDL_mixer developement
libaries (https://www.libsdl.org/projects/SDL_mixer/, under Binary).

For linux users, just install the following two packages using `apt-get`

```
libsdl2-dev
libsdl2-mixer-dev
```

Before running make on the project, double check the first few lines of the
`Makefile` and make sure you build the right version.

I used MinGW with gcc to build the project.

## Custom resolutions

If your preferred screen resolution doesn't show up in the screen resolution
menu, launch the game with argument "resolution *x*", and enter your screen
resolution dimensions in the fields marked by *.

## Issues with higher resolutions

`rottexpr` is capable of running at higher resolutions than the original release
of RotT, however this comes with a few issues.

1. Being able to see through walls when up against them/shrooms stretched screen
   effect. For this issue, visit "ADJUST FOCAL WIDTH" under "VISUAL OPTIONS",
   and raise the value until the issue disappears.
		
2. The game refuses to run at anything higher than 4k. 4k resolution is
   currently the limit set in code.
