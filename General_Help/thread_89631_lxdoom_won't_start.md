---
title: "lxdoom won't start"
date: 2005-11-13
forum: General Help
---

### Post by DaneM on 2005-11-13
Hi, everybody.  I'm pretty new to Ubuntu, so any help you can give me will be well-appreciated.

I've recently installed lxdoom and the shareware doom1.wad file, and I can play it great just as long as I give it the "-nosound" option.  If I don't give it that option, I get this:

[FONT="Arial"]LxDoom v1.4.4 ([http://lxdoom.linuxgames.com/](http://lxdoom.linuxgames.com/))
Z_Init : Allocated 6016Kb zone memory
 found /usr/share/games/doom/doom1.wad
IWAD found: /usr/share/games/doom/doom1.wad
LxDoom (built Apr  6 2005), playing: DOOM Shareware
LxDoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
M_LoadDefaults: Load system defaults.
I_SetRes: Using resolution 320x200
V_Init: allocate screens.
 found /usr/share/games/doom/boomlump.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/doom/doom1.wad
 adding /usr/share/games/doom/boomlump.wad

M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon -
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites
R_Init: R_InitPlanes R_InitLightTables R_InitSkyMap R_InitTranslationsTables
P_Init: Init Playloop state.
I_Init: Setting up machine state.
I_InitSoundGen: I_InitSound: Passing sound data to /usr/games/sndserv via pipe:
[/FONT]

...and it stops loading at that point.  I have to hit CTRL-C to get it to go back to the terminal.  I have verified that /dev/dsp and /dev/audio are present, and that snd-pcm-oss has been loaded.  Sound works in GNOME, but if I try to do, "cat /dev/urandom > /dev/dsp" (or > /dev/audio, which should produce a bunch of static from the speakers), I get nothing.

Any ideas?

Thanks!

--Dane

---

### Post by DaneM on 2005-11-20
*bump*

---

