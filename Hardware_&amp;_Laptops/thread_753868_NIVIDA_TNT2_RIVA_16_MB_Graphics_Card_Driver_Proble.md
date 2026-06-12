---
title: "NIVIDA TNT2 RIVA 16 MB Graphics Card: Driver Problem"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by peterkeyani on 2008-04-13
Hi

The old pc (NEC pentium 4/ 1.5 G/ 630 MB/ 1x160 GB plus 1x20 GB HD) which I installed ubuntu 7.10 on has a puny Nvidia TNT2 Riva 16 MB video card in it.

Without using the NVIDA driver which is offered during the OS installation the OS works ok but not great.

I tried downloading the NVIDA driver but it kills the computer.

Any ideas?

Thanks

Pete

---

### Post by peterkeyani on 2008-04-13
> **peterkeyani said:**
> Hi

I tried downloading the NVIDA driver but it kills the computer.

Pete

PS by kills I mean that after I restart the computer after the driver was downloaded and installed what happens is the pc stops dead after the first ubuntu screen. The spinning dot just stops and everything locks up.

---

### Post by wandalalakers on 2008-04-13
I recently removed a tnt 2 32mb card from a pc and upgrade to a 128mb nvidia.  I think I used the nv driver.  Try this.
I'm not sure if you already have the os on your machine or if you are dong a new install.
If booting up, do the 2nd option on the menu.  I'm at a windows pc right now so I can't tell you which screen.

dpkg-reconfigure xserver-xorg and select nv.
if you are able to boot into the os try downloading the envy program and installing 96.xx driver or 73.? or something like then when installing the nvidia driver manually using the envy program.
From what I remember, I didn't use the envy program with the pc that had the tnt2 card.

---

### Post by SoloSalsa on 2008-04-13
> **peterkeyani said:**
> The old pc (NEC pentium 4/ 1.5 G/ 630 MB/ 1x160 GB plus 1x20 GB HD) which I installed ubuntu 7.10 on has a puny Nvidia TNT2 Riva 16 MB video card in it.
Same here! P4 2.0GHz, 768MiB, "160gb", and OEM something-or-other TNT2 (I suspect it has 16 or 8 megs).  I've followed so many guides and tried so many commands and reinstalls, and I just gave up on it.  The best I got was 16bit acceleration at 800*600 pixels, and whenever I tried to increase resolution, I got xorg errors.  So I use the unaccelerated default configuration from the Ubuntu install.  Good luck with that.

---

### Post by youngheart80 on 2008-04-13
Moved to different forum.

---

### Post by Mike T. on 2008-04-15
I'm having a similar problem with a TNT2 M64 card as well.

I can get gnome to start (1024x768, 1200, 1024 or 1600 x1200) with no problems, however shortly after logging in the computer will freeze (even the animated cursor stops).  Most sure way to reproduce this is problem seems to be to open any window then open a couple of terminal windows.  The only solution appears to be to power off and reboot.  

Tried adding the line '    Option  "NoAccel"  "true" ' to xorg.conf as suggested elsewhere but it still hangs.  I think that there must be a problem with gnome using the nv driver with the TNT2 card .   

- I rebuilt my system using a minimal install and when I run just the xserver and an xterm I can open multiple terminal windows and it seems stable, but without a window manager you can't move the windows!)

- I have no issues with the same driver using an nVidia 5700 card (in a different box)

Going forward I plan on trying xserver with twm and upgrading to a second hand nVidia 5200 PCI card to see if that solves the problem.

Mike T.

---

