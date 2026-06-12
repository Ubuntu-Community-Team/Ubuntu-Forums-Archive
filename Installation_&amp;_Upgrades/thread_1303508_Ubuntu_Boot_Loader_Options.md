---
title: "Ubuntu Boot Loader Options"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by PaulyWally on 2009-10-28
Hello all,

I'm thinking about making the leap from Debian to Ubuntu.  Specifically, I'm looking at Ubuntu Studio.

One of the many things I like about Debian, is being able to easily place Grub on a floppy disk (or USB drive) during the initial installation.  I have reasons for doing this and I don't see that changing in the near future.

My question is, does the Ubuntu installation allow an option for this?  I want to give Ubuntu an honest try... but if it alters the boot sector on my hard drive in any way, it's not going to be a good thing as I have multiple operating systems on the computer.  Putting a new boot loader on the HDD (even temporarily) is going cause a lot of rework for me.  So for the Linux install, I need to specify where the boot loader is installed right off the bat.

Thanks!

---

### Post by phillw on 2009-10-28
> **PaulyWally said:**
> Hello all,

I'm thinking about making the leap from Debian to Ubuntu.  Specifically, I'm looking at Ubuntu Studio.

One of the many things I like about Debian, is being able to easily place Grub on a floppy disk (or USB drive) during the initial installation.  I have reasons for doing this and I don't see that changing in the near future.

My question is, does the Ubuntu installation allow an option for this?  I want to give Ubuntu an honest try... but if it alters the boot sector on my hard drive in any way, it's not going to be a good thing as I have multiple operating systems on the computer.  Putting a new boot loader on the HDD (even temporarily) is going cause a lot of rework for me.  So for the Linux install, I need to specify where the boot loader is installed right off the bat.

Thanks!

You can do a persistant instal of ubuntu onto a pen-drive (usb), is this what you're looking to do ?


Phill.

---

### Post by PaulyWally on 2009-10-28
> **phillw said:**
> You can do a persistant instal of ubuntu onto a pen-drive (usb), is this what you're looking to do ?


Phill.

Nope.  I want the OS and all programs installed on an internal HDD... I just don't want the boot loader (Grub, LiLo, or whatever Ubuntu uses) installed on the internal HDD.  I want to install the boot loader on external media like a floppy.  With this configuration, the computer will not even recognize Ubuntu as a bootable OS unless the floppy is inserted.

The Debian installer has an option for this and I'm hoping Ubuntu does also.

Thanks!

---

### Post by louieb on 2009-10-28
The alternate install CD uses the Debian installer. Don't know if Studio has an alternate CD download option. Ubuntu Studio can be added later to a normal Ubuntu install. 

On the live CD installer - on the Install summary page - advanced button - tell where to install GRUB  or not. But cant remember if it can create a boot floppy or not.

---

### Post by oldfred on 2009-10-28
Under manual install on the last screen where grub is installed is an advance button. I use that to install grub to the partition so I can chainboot. I have not tried using it to install to a floppy, but it does prevent the overwriting of the MBR. 

You also can use it to install to the MBR of other hard drives. I like to have different operating systems on different drives and each to be in the MBR so if a drive fails I can change boot order and still have a working MBR without having to find the liveCD.

---

### Post by davec64 on 2009-10-28
I've just been reading a post on GRUB2, this is new and will be installed with Karmic.
If you plan on using the version of Ubuntu Studio based on Karmic have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub2]("http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub2")

They might be able to answer your question specifically :)

---

