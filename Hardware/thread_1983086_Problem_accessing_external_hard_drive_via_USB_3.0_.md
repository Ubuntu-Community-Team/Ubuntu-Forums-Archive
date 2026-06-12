---
title: "Problem accessing external hard drive via USB 3.0 port"
date: 2012-05-19
forum: Hardware
---

### Post by rewyllys on 2012-05-19
To my desktop computer system, I've just added a Buffalo DS Axis 2.0TB External Hard Drive (HD-LBU3) and a PCIe USB 3.0 Host Controller Card.  The desktop computer is currently running on Linux Mint 11 (Katya), which is based on Ubuntu 11.04 (Natty Narwhal); the Linux kernel is 2.6.38-8-generic; and the desktop environment is GNOME 2.32.1.

When connected via the new USB 3.0 controller card, the external hard drive takes about a minute, after booting, to show up on my computer's desktop screen.  By itself, that delay would not bother me.  But, after about another minute, the HD-LBU3 icon disappears, as does the HD-LBU3 listing under Places.  And nothing I've tried enables the HD-LBU3 drive to be detected or accessed again till after a restart.

When connected via an older USB 2.0 port, the HD-LBU3 icon takes about a minute, after a reboot, to show up on the desktop, and it remains.  Accessing the 2.0TB external hard drive presents no problems during the rest of my work session.

So, I've concluded that Linux Mint 11 -- and, hence, presumably, Ubuntu 11.04 -- has a serious difficulty handling USB 3.0, at least via the PCIe USB 3.0 HC Card that I'm using.  

My questions are:  

[INDENT]1. Have other people encountered similar difficulties in handling USB 3.0 connections with Ubuntu 11.04?
[/INDENT]
[INDENT]2.     Does Ubuntu 12.04 handle USB 3.0 connections satisfactorily?
[/INDENT]

---

### Post by ahallubuntu on 2012-05-19
The kernel needs to have a good driver for the specific USB 3.0 card you have added.  It's possible your kernel does not support this card properly.

You might look at /var/log/syslog right after the drive has disappeared to see if anything has been reported after that.

One easy thing you should try: boot a Ubuntu 12.04 LTS live CD on this computer and see how it handles the external drive.  If it works without any problems, then you might try to find an updated driver for your USB card's chipset, build the module, and load it in place of the module in your current kernel.

From Ubuntu 11.04 terminal type

sudo lspci

and see if you can figure out which one is your USB 3 card.  FYI, NEC-based cards tend to work better in Linux than Via-based cards in my experience.

---

### Post by rewyllys on 2012-05-19
Ahallubuntu, thanks for your helpful suggestions.

The "sudo lspci" command yields, *inter alia*, "USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)", so the 3.0 card is being recognized.  

I'll try the Ubuntu 12.04 Live CD technique later this evening.  And I'll also try searching for a better driver for the card.

Again, thanks.

---

### Post by Azyx on 2012-07-10
> **rewyllys said:**
> Ahallubuntu, thanks for your helpful suggestions.

The "sudo lspci" command yields, *inter alia*, "USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)", so the 3.0 card is being recognized.  

I'll try the Ubuntu 12.04 Live CD technique later this evening.  And I'll also try searching for a better driver for the card.

Again, thanks.

How did it go? My 3.0-speed have disappeared :( Just when I installed I have same speed as it was an internal drive. Now I only have approximate 20MB/s (USB 2.0) Have Ubuntu 12.04 on E45M1-M pro mother board.

**[COLOR=Red]EDIT: After fix some error on the NTFS-disk, USB 3 speed have come back :) [/COLOR]**

---

### Post by americanman28 on 2012-07-12
usb 3.0 is not all there yet in ubuntu

---

### Post by Azyx on 2012-07-12
> **americanman28 said:**
> usb 3.0 is not all there yet in ubuntu

Strange. [http://en.wikipedia.org/wiki/USB_3.0](http://en.wikipedia.org/wiki/USB_3.0)

---

