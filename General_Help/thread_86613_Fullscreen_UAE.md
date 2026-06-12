---
title: "Fullscreen UAE"
date: 2005-11-05
forum: General Help
---

### Post by Wrosmo on 2005-11-05
I have been running UAE for a week now, but I cannot get it to work in fullscreen.
I use a configfile (pasted in at the bottom of this post), but it only runs the games in a window. I have tried running UAE with the sudo command and from the root terminal. 

Any suggestions?

Wrosmo


a500.conf:

joyport1=kbd2
cpu_speed=real
cpu_type=68000

kickstart_rom_file=KICK13.ROM

sound_output=normal
sound_bits=16
sound_channels=stereo

chipset=ecs

fastmem_size=0
chipmem_size=1
a3000mem_size=0
z3mem_size=0
bogomem_size=0
gfxcard_size=0

gfx_width=800
gfx_height=600
gfx_linemode=double
gfx_color_mode=16bit
gfx_center_vertical=true
gfx_center_horizontal=true
gfx_fullscreen_amiga=true

---

### Post by Wrosmo on 2005-11-07
I figured it out myself. UAE 0.8.22 (as in Ubuntu repositories) is to old and cannot do fullscreen (it is supposed to do fullscreen, but it doesn't).

E-UAE does it without any trouble. E-UAE is a fork of th old UAE. 

Wrosmo

(UAE - U(nix, ltimate, biqious) Amiga Emulator)

---

### Post by marx2k on 2007-01-11
I am using E-UAE 0.8.29-WIP3 and I cannot figure out how to make this go FUllScreen

I thought F12 + s would do it but it doesnt

---

### Post by schmildo on 2007-12-18
try F12 + g
if F12+s isn't working, and i found I had to press F12 first, then g.

(it was wierd, 's' was working for me before)

---

