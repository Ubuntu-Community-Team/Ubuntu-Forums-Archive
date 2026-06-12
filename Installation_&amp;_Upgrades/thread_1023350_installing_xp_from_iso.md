---
title: "installing xp from iso"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by wimpytx on 2008-12-27
how can i install xp via an iso. within Ubuntu i do not have dvd/cd drive as im on an msi wind. i also have ausb flash drive (2gb).
Also i need a real instal not virtual-box or the like.

---

### Post by inobe on 2008-12-27
you cannot install xp within ubuntu without a virtual machine.


it will be the same the other way around.


you could dual boot, you cannot run both operating systems simultaneously, this is only possible via virtual machine.

---

### Post by -kg- on 2008-12-27
> how can i install xp via an iso. within Ubuntu i do not have dvd/cd drive as im on an msi wind. i also have ausb flash drive (2gb).
Also i need a real instal not virtual-box or the like.

I'm not quite sure what you are asking.  Are you asking how to install XP via an .iso image, and that within Ubuntu you do not have a CD/DVD ROM?  Or are you asking if you can install XP from an .iso *within* Ubuntu?

If you have a CD/DVD drive on your machine (and if you can set it as a boot device in your BIOS) you should be able to burn the .iso to a disk (if you can't do it locally, take a copy of the .iso to someone who can and have them burn it for you) and then boot to the disk and install.

If you don't have a CD/DVD drive on your machine, I'm not sure what to tell you.  I know that Ubuntu can be installed from a flash drive device, but I don't know about XP.

---

### Post by skeetre on 2009-01-01
This might be after the fact... but it is possible. You can extract the contents of the iso to the usb drive, then make the usb drive bootable and run the xp install from the usb drive.

I don't know the page with the instructions, but you can google for it, something like, "install xp from thumb drive" 
You'll probably get instructions for how to do it from windows, but then you can google for linux instructions to "linux make thumb drive bootable" or some such.

Or you might be able to use a virtual machine to start an install to a real partition, then change the grub menu to boot from that partition and continue the install normally outside the virtual machine.

let me know if you need help still.

---

