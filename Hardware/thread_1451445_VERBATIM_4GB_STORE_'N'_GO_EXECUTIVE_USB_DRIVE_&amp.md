---
title: "VERBATIM 4GB STORE 'N' GO EXECUTIVE USB DRIVE &amp; Ubuntu"
date: 2010-04-10
forum: Hardware
---

### Post by aggelos_930 on 2010-04-10
[http://www.verbatim-europe.co.uk/en_1/product_store-n-go-usb-executive-4gb_12036.html](http://www.verbatim-europe.co.uk/en_1/product_store-n-go-usb-executive-4gb_12036.html)

I want to buy this flash drive but is it compatible with ubuntu?
As I see at the verbatim site it has some kind of encryption software.
Is there any chance that i would be unable to use the device because of this software's incompatibility with ubuntu?

---

### Post by yelvington on 2010-04-10
The specs for that device clearly say that it works with:

Windows ME, 2000, XP, Vista
Mac OS 9 or higher
Linux 2.4.0 or higher
Compatible with Windows 7

Generally, devices like this come formatted with FAT filesystems and preloaded with Windows software. You can't make use of the Windows software. You can just delete the software and, if you want, reformat the device using any filesystem supported by Linux, or even partition it.

---

### Post by aggelos_930 on 2010-04-10
I see. It should be like my WD external HDD. You can store data but you can't use their software.

---

### Post by KittyChunk on 2011-01-15
I'm having problems with a Verbatim V-Secure Executive USB drive in Ubuntu. This drive has a separate small partition containing some (Windows-only, sigh) login and encryption software, which is all that mounts when the drive is plugged into an Ubuntu machine. On a Windows box, the software then autoruns, asks you for a password, and then mounts the rest of the drive space as a separate partition.

In Ubuntu, fdisk/gparted etc don't even see the small partition after the drive has mounted (it only mounts read-only), so no dice reformatting it from linux. In Windows, the partition structure on the drive is also locked even after you've logged in with the password, so Windows' built-in tools aren't able to delete or reformat the partitions either

This drive was given to me as a gift, but it's basically a doorstop unless I can find a way to reformat it for normal use in Ubuntu :). Any suggestions?

-q

---

### Post by dandnsmith on 2011-01-15
Your best bet is to try to ignore what is there and create a new partition table (or treat the device as a single 'partition', and format that as FAT).

One problem is that Windows doesn't like partitions on these USB sticks, and can give problems handling them. I'd got into linux, unmount any bits on the stick, and then format the whole device after creating the FAT filesystem. You may need then to redo the op under Windows, just to get it properly usable.

Sorry - incoherent, but I hope it helps.

---

