---
title: "installing OS on a very old laptop without a working cd-drive"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by Dan_Dranath999 on 2008-04-14
The situation is this:

I'm trying to install Fluxbuntu on a laptop. The laptop has a cd drive, but it's not working properly, so it won't let me install the OS. 

¿Is there a way of installing it from a USB drive? (there's a floppy drive, tho)

¿Or should i look the way of connecting my desktop CD-drive to the laptop? (i assume there's a ide converter like the ones used with 2.5 hard drives)

Thanks, for any ideas.

---

### Post by logos34 on 2008-04-14
Assuming you've got some version of windows on this old lappy, try this howto:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
(--> UNetbootin, or 'CD image approach')

Chances are the machine cannot boot from USB, but a flash drive will come in handy transferring the ubuntu .iso to the hard disk.

---

### Post by Dan_Dranath999 on 2008-04-21
Nope. no windows.

The cd-drive works with some cds (it installed Damn Small Linux without errors) the ones using 50 Mb or so, i suppose.

Using a  big distro cd, will give errors. Even is the cd is checked in another machine.

¿Can't i just connect a regular cd-drive in there with some kind of converter?

---

### Post by Limbic on 2008-04-21
> **Dan_Dranath999 said:**
> Nope. no windows.

The cd-drive works with some cds (it installed Damn Small Linux without errors) the ones using 50 Mb or so, i suppose.

Using a  big distro cd, will give errors. Even is the cd is checked in another machine.

¿Can't i just connect a regular cd-drive in there with some kind of converter?

Do you get an error that says something about Isolinux, along with a disk error?  It may be an issue with your BIOS not being able to recognize and work with Isolinux, which could explain why nothing but Damn Small Linux works.  DSL has a Syslinux .iso that works fine with older computers, as it's an issue with the BIOS and not the CD drive itself.

What kind of computer is it?  I've been messing around installing Linux on an old Dell Inspiron 2600 and ran into the same errors.  The best starting place to help would probably to just give the brand and model name of the laptop you're working with, then work from there.

---

### Post by Dan_Dranath999 on 2008-04-26
i tried to use Xubuntu alternate cd, but it said the cd had errors -tested the cd on my desktop, and it was perfect-

dont know the brand of the laptop, don't have cd, documentation, nothing.. (it's supposed to be 5 o 6 years old: 125 mb RAM! Floppy drive, it came with XP installed, but had problems from the beginning) 

The closer i got, was copying the contents of a fluxbuntu cd to a External USB hardDrive, then copying it to the internal hard drive, adding it as an option into GRUB, ¡And it starts! but fails because it looks for the rest of the files from the cd-drive, which is empty... (some say its possible, but you got to mount the cd content at the middle of the installation process -and the disc content must be in a separate partition-)

---

### Post by Dan_Dranath999 on 2008-05-01
any ideas?

---

