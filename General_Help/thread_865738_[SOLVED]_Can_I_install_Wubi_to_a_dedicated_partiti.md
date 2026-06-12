---
title: "[SOLVED] Can I install Wubi to a dedicated partition, but keep the windows bootloader"
date: 2008-07-20
forum: General Help
---

### Post by nuclearpidgeon on 2008-07-20
Hi

I want to use wubi to install to a dedicated partition, but I want to keep the windows boot loader setup.

Let me rephrase this in the form of an ideal boot process flow-chart:

Power ON -> BIOS - > HD0 (Windows Boot loader, with Windows and Ubuntu options) -> Choose Ubuntu option -> HD1/2 (Ubuntu extended partition) -> GRUB -> ubuntu

So the windows boot loader simply points the linux partition, where grub is installed.

I want to do this so I can benefit from hibernation, but also have the ability to easily uninstall Ubuntu, if needed (it's easier remove the Ubuntu entry in the windows boot loader rather than use an XP recovery cd to re-install the XP bootloader over the top of GRUB)

Any ideas?

---

### Post by ago on 2008-07-21
Grub is a better bootloader than the windows one and in any case fixmbr from windows recovery console will restore the windows bootloader. It is possible, but I do not recall on top of my head if the Live CD installer allows you to install grub to a partition as opposed to the MBR. Check that.

---

### Post by nuclearpidgeon on 2008-07-21
> **ago said:**
> Grub is a better bootloader than the windows one and in any case fixmbr from windows recovery console will restore the windows bootloader. It is possible, but I do not recall on top of my head if the Live CD installer allows you to install grub to a partition as opposed to the MBR. Check that.

There is an advanced option on the final page of the installer that says where you can install the bootloader. By default it is set to hd0,0, but you can change it to the different partitions (/dev/sda, /dev/sda1).
Now all I need is a way to install an Ubuntu/GRUB entry in the windoze bootloader...

EDIT:
Sorry, forgot to add that I tried to re-install the bootloader, but the windoze XP CD said it couldn't find any available hard-drives...
And if I had this set up it would just be much easier to uninstall anyway.

---

### Post by nuclearpidgeon on 2008-07-24
This is my current boot.ini in windows

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```If I added:
```
multi(0)disk(0)rdisk(0)partition(3)="Ubuntu GRUB"
```would it work?
I would have installed GRUB to the extended partition (partition 3), but are there any other options I need?

---

### Post by ago on 2008-07-24
[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)

---

### Post by nuclearpidgeon on 2008-07-24
> **ago said:**
> [http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)

Hmm, very confusing. I think that the instructions are for booting Linux from a pen-drive?

To chain-load grub, do I need that Linux.bin file, or can I just point the windows boot-loader to the Ubuntu partition? Because if you need to make a image file that is the boot sector, every kernel update I'd need to re-update the image.

I'll try the method I listed above, with the link to the partition. It shouldn't do any harm to my windows install...

---

### Post by nuclearpidgeon on 2008-07-27
Got it working. The wiki was right, thanks Ago.
You need to first install the bootloader to the main ubuntu partition, or the partition that contains the /boot folder. from there, you need to make a linux.bin file which contains the MBR/Bootloader from that partition, and then put it on the windows hard-drive and point the windows bootloader to that file.
Thanks Ago!

---

