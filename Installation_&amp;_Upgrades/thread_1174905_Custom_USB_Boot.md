---
title: "Custom USB Boot"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by pyre on 2009-05-31
I have a 32GB thumbdrive and I've come up with an idea that I've been tossing around for a couple of days and now I want to see if it's possible.

I want to create a custom Live USB Install... But I want to also back up my current /home to a partition on the thumbdrive so that I can use my Live distro to access it.

Basic things I want:
 * To be able to boot up the live distro on most computers that are capable of booting from usb. (this is obviously met by the basic ubuntu setup, though I may want to mess with drivers a bit... like blacklisting pcspkr)
 * To be able to use the live distro as a way of accessing all of my data and having the required software to access it.
 * To be able to setup users on the distro with similar UIDs/GIDs so that I don't have a permissions nightmare if I have to sync from the backup to my laptop's /home (I don't even know if this is possible)
 * Be able to customize (mostly just add to) the basic software install so that I have non-standard ubuntu packages on there as well as 3rd-party packages like TrueCrypt... But I want these packages to also install to whatever host I'm installing to.

I know that most of these would be satisfied by just installing Ubuntu to the usb drive, but I also want it to work as a Live Distro so that I can install Ubuntu to the computer I used to boot it up and as far as I know, the required files/software are not installed when installing Ubuntu.

There are plenty of guides/etc on how to add additional software to a live cd and a couple of guides on getting a live cd onto usb drive (for a live usb install). But is there a way that I don't have to do this process?
 * copy files iso->disk
 * muck around with files and add software
 * convert files -> iso
 * mount iso; copy files iso->usb

My other major question is whether or not there is a way to create users on a live cd (which I didn't see in any of the tutorials). If not, is there a way for me to take a standard install and give it the ability to install the distro to other computers?

What are my options?

---

### Post by Old_Grey_Wolf on 2009-05-31
If I understand what you want, and if you have 8.10 or 9.04, try the menu "System > Administration > USB Startup Disk Creator". It will ask you to select the amount of reserved extra space to store documents and settings. I give mine half the space available. I have been able to set up user accounts, save hacks for wireless adapters, and so on.

I hope this is what you are looking for.

---

### Post by pyre on 2009-05-31
> **Old_Gray_Wolf said:**
> If I understand what you want, and if you have 8.10 or 9.04, try the menu "System > Administration > USB Startup Disk Creator". It will ask you to select the amount of reserved extra space to store documents and settings. I give mine half the space available. I have been able to set up user accounts, save hacks for wireless adapters, and so on.

I hope this is what you are looking for.

Ok. But the way I understand it, that is using something like UnionFS... in which the FS is just storing the changes to the read-only FS on a separate partition and when mounted together, the driver merges the two file systems into one on top of each other.

I want something that I can mount without booting into the USB Installed Distro and then do an rsync of my current /home partition to a partition on the USB Thumb drive so that my /home on the thumbdrive is the same as the one on my laptop.

Would I be able to install packages when booted into the USB Install, and then have those packages become part of a default Ubuntu install, were I to use the USB Install to reformat/reinstall Ubuntu on my laptop for instance?

---

