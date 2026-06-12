---
title: "gnome screensaver woes - need help"
date: 2008-07-22
forum: General Help
---

### Post by abyssius on 2008-07-22
My computer has been running hardy 8.04 for amd64 flawlessly since it was released. The upgrade from gutsy was smooth and I've applied all subsequent updates with no problems. I've applied a custom theme via the Art Manager menu, and still had no problems. I tried to select a gnome screen saver for the first time (I used to let the screen go blank). I was scrolling through and watching the screen saver previews when the computer locked up as I passed the mouse over a particular one. The screen went blank, then the computer resorted to the login screen. I was able to log back in and every thing seemed fine. However, every time I try to return to the screen saver menu the same thing happens. - the screen locks up for a second, then the computer reverts to the login screen. This also happens if I let the computer idle for a few minutes. It is not a complete crash, since I can log back in and the computer seems fine. 

Below is the only error message I found so far:

[INDENT]dmesg | grep screensav
[ 1244.661891] gnome-screensav[26671]: segfault at 3d4 rip 7f41f3a56d51 rsp 7ffffbc61150 error 4
[ 4671.560782] gnome-screensav[22072]: segfault at 3d4 rip 7fae6e288d51 rsp 7fff76490980 error 4
[ 5661.763826] gnome-screensav[7191]: segfault at 3d4 rip 7f6b640afd51 rsp 7fff6c2b7780 error 4[/INDENT]

I'm assuming that I inadvertently selected a corrupt screensaver file, or one that my video card can't handle. Anyway, doe anyone know what's happening, or is there a command line way to disable the screensaver, so I can halt the crashes?

My computer: Sempron 3000+, ASROCK MB, Prism wireless card, ATI video adapter using std. ati X driver, 80gig hdd IDE, 512mb RAM, soundblaster audigy, NEC 20X DVD-RW IDE.

---

### Post by y-lee on 2008-07-22
Hi sorry about your problems.

I don't know what is happening but the command below might disable the screen saver. I make no guarantees but it works for me.

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
```

---

### Post by abyssius on 2008-07-22
Thanks for response y-lee. I entered your command, then I went to select the screebsaver menu [Preferences/Screensaver]. As soon as I do this, It seems like GDM(?) or X server(?) crashes and I get sent to the login screen. Weird.

---

### Post by y-lee on 2008-07-22
hmmm

try reinstalling the screensaver. Open Synaptic Package Manager under **System --> Administration** and search for *gnome-screensave*r. When you find it right click and choose **Mark for Reinstallation**

---

### Post by abyssius on 2008-07-22
Everything appeared to go okay with the re-installation via synaptic, but of course as soon as I try to access the screensaver menu something crashes and I'm presented with the login screen. Is there a command that i can try to actually show what is crashing? I beginnning to suspect the fault might not be solely in the screensaver program.

---

### Post by abyssius on 2008-07-22
It seems like when I use dmesg the segfaults keep adding up, Unfortunately, I don't have a clue what it is telling me...

dmesg | grep screen
[ 1244.661891] gnome-screensav[26671]: segfault at 3d4 rip 7f41f3a56d51 rsp 7ffffbc61150 error 4
[ 4671.560782] gnome-screensav[22072]: segfault at 3d4 rip 7fae6e288d51 rsp 7fff76490980 error 4
[ 5661.763826] gnome-screensav[7191]: segfault at 3d4 rip 7f6b640afd51 rsp 7fff6c2b7780 error 4
[11551.308818] gnome-screensav[13978]: segfault at 3d4 rip 7fa65472ad51 rsp 7fff5c9326a0 error 4
[13520.419171] gnome-screensav[16021]: segfault at 3d4 rip 7fe251999d51 rsp 7fff59ba4070 error 4

---

### Post by y-lee on 2008-07-22
A little googling around and I have found several people reporting a similar problem and two related bug reports on launchpad, see [ gnome-screensaver segfault]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/223015"). And unfortunately no solution so if reinstallation doesn't work I can only suggest not using gnome screen saver for now and wait for this bug to be fixed  which i would assume in time it will be. You could install xscreensaver and use it, I use it when i use DWM (a rather simple windows manager I use sometimes). I have never tried using xscreensaver in gnome tho but it should work.

Not sure why this bug is effecting your system but most systems are unaffected. May have some thing to do with your hardware, but regardless it is buggy behavior and the program shouldn't segfault no matter what.

---

### Post by abyssius on 2008-07-22
Thanks for your assistance, y-lee. I kinda figured that this must be a bug. I'm a little disappointed since I was feeling quite complacent about Ubuntu, having been through some early traumas since I adopted it in january. However, as you wisely point out - I'll continue to truly search for the Way, both in Ubuntu and in my spiritual pursuits.

---

### Post by abyssius on 2008-07-22
UPDATE: I uninstalled gnome-screensaver, installed xscreensaver but screensaving continues to generate segfaults and send me back to the login screen. Apparently this bug goes beyond gnome screensaver, as described in  [gnome-screensaver segfault]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/223015").. see below

[ 1244.661891] gnome-screensav[26671]: segfault at 3d4 rip 7f41f3a56d51 rsp 7ffffbc61150 error 4
[ 4671.560782] gnome-screensav[22072]: segfault at 3d4 rip 7fae6e288d51 rsp 7fff76490980 error 4
[ 5661.763826] gnome-screensav[7191]: segfault at 3d4 rip 7f6b640afd51 rsp 7fff6c2b7780 error 4
[11551.308818] gnome-screensav[13978]: segfault at 3d4 rip 7fa65472ad51 rsp 7fff5c9326a0 error 4
[13520.419171] gnome-screensav[16021]: segfault at 3d4 rip 7fe251999d51 rsp 7fff59ba4070 error 4
[20862.419210] xscreensaver-gl[14100]: segfault at 3d4 rip 7fb196a88d51 rsp 7fff9ec912b0 error 4
[20869.323477] xscreensaver-gl[14230]: segfault at 3d4 rip 7f05cd267d51 rsp 7fffd5471a50 error 4
[23018.024737] xscreensaver-gl[19339]: segfault at 3d4 rip 7fb9819add51 rsp 7fff89bb81e0 error 4

---

### Post by y-lee on 2008-07-22
Curious and confused.

Hmm might be a video card/driver issue. What video card are you using and have you installed any "restricted drivers" for it? Are you using desktop effects, Beryl or Compiz?

Segment faults could also be a memory issue have you run memtest to check your memory?

Does any other application give segment fault errors that you know of?

---

### Post by abyssius on 2008-07-23
I'm using an older ATI Raedeon RV100 QY [Radeon 7000/VE] PCI card with 256mb video RAM. I'm using the standard driver for X-server (ati) - no restricted drivers, etc. I noticed that a ATI Raedon was involved in the bug report also. I'm beginning to think that the problem may be 3-D rendering using the basic ATI driver and older ATI cards. I can't use the new ATI driver because it apparently doesn't support my chipset.

I'll try replacing my video card with a nVidia card I have in my parts bin to see what happens.

---

### Post by abyssius on 2008-07-23
UPDATE: I replaced the ATI Raedon with a NV11DDR [GeForce2 MX200] AGP video card and the screensaver segfault problem appears to be fixed. So apparently, it is the combination of my ATI card and the standard ati X driver that was causing the problem. I can't say that it is specific to my chipset, since others with different ATI Raedon chipsets have reported the problem also.

---

