---
title: "Problem installing Ubuntu"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by DangerBoy on 2006-04-24
Hi guys, new to this forum just joined today, well i have and old dell latitude laptop, pentium 2 266mhz, with 128 mb ram, it had Windows NT, I later upgraded to Win98 and then to XP, but i would like to install ubuntu 5.10 but the cd doesn't boot at startup, is there any other way i can force boot it?](*,)

---

### Post by Nikusan on 2006-04-24
[QUOTE=DangerBoy]Hi guys, new to this forum just joined today, well i have and old dell latitude laptop, pentium 2 266mhz, with 128 mb ram, it had Windows NT, I later upgraded to Win98 and then to XP, but i would like to install ubuntu 5.10 but the cd doesn't boot at startup, is there any other way i can force boot it?](*,)[/QUOTE]

Is your BIOS set to boot from the CD drive? If so perhaps the disc is a dud. Is it possible for you to test with a different disc?

---

### Post by Sef on 2006-04-24
> pentium 2 266mhz, with 128 mb ram

With your ghz and ram, I would do a server install first, then install a lightweight window manager, e.g., fluxbox (the lightest), xfce (xubuntu), icewm.

From the terminal, server type this:

sudo apt-get update

sudo apt-get install window-manager

---

### Post by RRS on 2006-04-24
You probably have to make the CD drive your first boot device in BIOS.

Before windows begins to boot you should have a few seconds with a Dell logo or something "non-windows" on the screen, try esc or F2 during this.

I seem to recall one of these as being used by Dell to access the BIOS before windows boots but if neither works  you may have to try contacting Dell.

Good luck and welcome aboard. :)

---

### Post by DangerBoy on 2006-04-24
Hi yes it booted win 98 and XP from the rom, the ubuntu cds are originals shipped to me,how else could i boot it?

---

### Post by DangerBoy on 2006-04-24
[QUOTE=Sef]With your ghz and ram, I would do a server install first, then install a lightweight window manager, e.g., fluxbox (the lightest), xfce (xubuntu), icewm.

From the terminal, server type this:

sudo apt-get update

sudo apt-get install window-manager[/QUOTE]
it 266 mhz dude, just starting off...
the primary booting device is the cd rom, so i am abit confused here....
:confused:

---

### Post by Sef on 2006-04-24
When you start type in server then enter.

ubuntu, if it installs on your system will be very slow.

---

### Post by RRS on 2006-04-24
> ubuntu, if it installs on your system will be very slow.

I believe the main concern here is the amount of ram instead of the cpu speed.

> When you start type in server then enter

First he has to be able to boot from the install disc. 

I haven't heard of any problems with the discs from Shipit but anythings possible. Are you able to download and burn an ISO image? (not referencing your abilities but rather I-net connection and a CD burner)

---

### Post by lmierzej on 2006-04-24
Hi,

bios in your computer is using older standart for booting cds. A bootable CD-ROM has a special layout that is detected by the BIOS boot loader code, and executed if it conforms the specifications.

Ubuntu cds are using eltorito, but your bios doesn't support it. But don't worry :)

If you have floppy just use Smart Boot Manger (install it on floppy, boot this floppy and then, from this floppy, cd with ubuntu).

You will find SBM here - [http://btmgr.webframe.org/](http://btmgr.webframe.org/) :)

Good luck,
lmierzej

P.S I don't know why most people on this forum dosn't answer questions, they are writing useless things :(

---

