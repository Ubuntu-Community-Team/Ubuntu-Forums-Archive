---
title: "Can't see all drives on new install gui??"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by webkris on 2009-03-29
Background:
Machine with 3 HDD's
HD1 setup with XP
HD2 setup as space NTFS
HD3 setup with Xubuntu.

Now the reason I was running xubuntu is because I had some dual head monitor and driver issues. I just recently wanted to give standard 8.10 Intrepid another go on my desktop and found that with the low video settings it would boot. I load the NVidia drivers I need, everything is sweet to ditch Xfce. I am in fact - WRITING THIS POST from the Live session on my machine.

I backup my /home and I'm ready to install.
I Double click Install from the desktop, and only see:
/dev/sda
/dev/sdb

[IMG]http://planetkris.com/misc/Ubuntu/install_partition.png[/IMG]

When I run a sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf887fc35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a3d0781

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80000040960 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51425a7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9324    74894998+  83  Linux
/dev/sdc2            9325        9726     3229065    5  Extended
/dev/sdc5            9325        9726     3229033+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```
[B]
How do I go about installing Ubuntu onto my 80GB /sdc?[/B]
Why can't I see it?
Do I need to worry about going over my grub setup? Currently on /sda.

Thanks for the help!
- Kris

---

### Post by dandnsmith on 2009-03-30
You don't need to worry about your grub setup - it won't have any bearing on this oddity.

I don't know why the install didn't show sdc as a partitioning possibility - after all fdisk does show it, as you demonstrated.
It cannot be because the HDD is full - after all the other two are, as well.
Could it be just that it cannot cope with more than 2?

---

### Post by webkris on 2009-03-30
Interesting isn't it...

I really don't want to format or re-partition the drive manually trying stuff and get my PC into a situation where I can't install and I can't go back. Well - I guess I could go back to XP :p

Can someone help with what I should do next?
- Kris

---

### Post by Mark Phelps on 2009-03-31
It's going to involve some work, but the SAFEST option would be to disconnect the other drives, leave only the third drive connected, change your BIOS to boot from that drive, insert the Ubuntu CD -- and install entirely to the third drive.

That will install GRUB to the MBR of that drive.

Afterward, you would reconnect the other drives but still boot from the third drive.  You will need to manually add an entry to GRUB for XP.

But the advantage in this approach is that you can experiment all you want during the Ubuntu install and not risk ANY damage to your XP installation.

---

### Post by webkris on 2009-03-31
Okay - Did it...
Pulled the IDE cable for the XP and the second drive.
Left the 80GB (*drive 3*) and the CD drive attached.
Dropped the Ubuntu CD in - booted. Machine saw the 80GB drive.
Installed Ubuntu. :D Yay!

Hooked up the IDE drives again.
I figured that I would see the OLD Grub menu for Xubuntu (*old install*), etc.
What I got was just the NEW menu for the new install.
I ran - gedit /boot/grub/menu.lst and tried adding the XP...
no dice.

**Then I Panicked... **
I booted the machine with an XP CD and ran a: fixmbr
The machine booted XP no problem. :| yay...

So NOW - I have a fresh install of Ubuntu on the 3rd 80GB drive that I can't access. :( I tried to install Grub...

Here's what my fdisk now looks like:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf887fc35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a3d0781

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80000040960 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51425a7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2432    19535008+  83  Linux
/dev/sdc2            2433        9726    58589055   83  Linux

```

I noticed I now have a STAR * next to the 80GB drive.
What I want to do is this:
1. Set the 3rd HDD to not bootable (get rid of the star? set non-bootable?).
2. Re-install grub on the 1st drive (the XP drive). It's currently installed on the 3rd drive.
3. Get it so that I can once again boot XP or Linux...

Thanks!
- Kris

---

### Post by dandnsmith on 2009-04-03
I'm a little confused - do you now have 2 separate ways of invoking grub, which work, for the different installs?
Also, did you have the XP disk as the booted disk for one of these at one stage?

Comment - you really don't have to worry about the 3rd HDD being marked as having a bootable partition - grub doesn't care a toss about that (only the Windows bootloaders do).

Comment 2 - some time ago it used to be the case that you couldn't install the grub boot files on an NTFS partition, as grub didn't have the tools to recognise NTFS. This may have changed - if it hasn't, then you'll need expertise to get stuff set the way you say you want it. I'm not sure I could say how to do it without experimenting on a live system.

---

### Post by webkris on 2009-04-05
My setup right now:
IDE0
1 - 120GB Windows XP
2 - 320GB NTFS Space

IDE1
1 - 80GB Ubuntu
2 - Sony CD/DVD

* If I have IDE0 connected only (the cable to the 2 drives) my system will boot into Windows XP.
* If I have both IDE0 and IDE1 connected, my system will boot into Windows XP.
* If I have IDE1 connected only, my system will boot into Ubuntu.

How should I re-install grub with all the drives connected - so that grub can see my Windows XP boot and my Ubuntu boot? - and boot them. :)
- Kris

---

### Post by dandnsmith on 2009-04-06
My personal choice would be to get the Windows loader to do the job of booting ubuntu.

To do this, you need to have all the drives connected, use a liveCD to boot, and install the grub boot stuff on that 3rd drive.
Then copy the grub bootloader to your main XP drive as an ordinary file to be executed, and add an entry to the Windows boot.ini (using XP) to load the grub which can pull in Ubuntu.

As a precaution, save the current content of the first block of the first drive before you do the grub install (just in case you didn't get it right first go).

The other route, getting grub to activate Windows, is for me a bit more chancy (as I don't know that you can successfully install on an HDD with only NTFS filesystem(s).

---

