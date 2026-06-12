---
title: "Install Ubunto on Dell C400 that I'm locked out of"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by gnoel on 2008-12-05
My situation is this:

Dell C400 laptop
No bootable cd rom, floppy drive or usb
WinXP installed but I can't log in because it is password protected

A previous thread discussed this same scenario, only with an XP partition that could be logged in to:

[http://ubuntuforums.org/showthread.php?t=858830&highlight=c400]("http://ubuntuforums.org/showthread.php?t=858830&highlight=c400")

Wubi will therefore not work, nor will any of the other "no CD" options listed.

My idea is to remove the hard drive and use a USB-to-IDE/SATA cable to hook up to my desktop machine, running 8.04 LTR.  Then I will format the hard drive and load it with the Live CD data before reinstalling it in the laptop.

Can I use UNetbootin to create the bootable HD as if it were a USB stick?

Or am I overlooking a more direct and easy approach?  There is a "Cardbus NIC" boot option on the BIOS, but I can't figure out how to make use of this.

Thanks in advance!

---

### Post by ozzcky on 2008-12-08
I was able to do a net install of Ubuntu on a c400 using this tutorial. You'll need to have an XP box on your network to do it.  I'm actually using 7.10 on my c400 as I couldn't get compiz to run with anything newer. 

[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows]("http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows")

---

### Post by gnoel on 2008-12-08
Sounds promising!  Thanks for the tip.

---

