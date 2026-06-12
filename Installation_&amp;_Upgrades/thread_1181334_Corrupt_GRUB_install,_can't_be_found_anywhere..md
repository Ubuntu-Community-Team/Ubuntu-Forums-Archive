---
title: "Corrupt GRUB install, can't be found anywhere."
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by ncalvin on 2009-06-07
Today I decided to make a new partition in my internal HDD for my desktop for the purpose of running Jaunty. I attempted to install from the CD, and things ran dandy until 94%, at which point an error message told me that GRUB failed to install, and that this was a fatal error.

So I tracked down some solutions on my laptop whilst running Ubuntu from the CD on my desktop. I have come across multiple "solutions", none of which have fixed the problem. 
"find /boot/grub/stage1 yields an Error 15
"find /grub/stage1" has the same result.
I tried the SGD and got a variety of error messages.

As for my setup, I am running Vista 64-bit on a 1TB partition, with the rest of the 1.5TB drive split off for Ubuntu. I also have a 1TB external connected via e-SATA (though I doubt this is relevant). I'm running in circles, making no progress, and am frankly completely fed up. It would appear that GRUB simply cannot be installed on my system. 

If anyone has a viable solution, I'd love to hear it. I had no such issues a couple of years ago running Feisty on Vista 32.

---

### Post by merlinus on 2009-06-07
The find grub commands do not work because grub is not installed.

Boot from the live cd, open a terminal, and post output of:

```

sudo fdisk -l

```

---

### Post by ncalvin on 2009-06-07
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x067e7f80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ebf7bb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      132611  1065194492    7  HPFS/NTFS
/dev/sdb2          132612      182401   399938175    5  Extended
/dev/sdb5          132612      181177   390106363+  83  Linux
/dev/sdb6          181178      182401     9831748+  82  Linux swap / Solaris
```

---

### Post by ncalvin on 2009-06-07
The exact phrase (occurring at 94%) is "Executing 'grub-install (hd0)' failed. This is a fatal error."

---

### Post by ncalvin on 2009-06-07
An to make it even more fun, if I try to boot Ubuntu through FreeBCD, it opens up GRUB4DOS instead.

---

### Post by merlinus on 2009-06-08
[SIZE=1]This may help.  And I notice that you cross-posted this issue.  It only leads to confusion and doubled efforts.  IMFFHO....[/SIZE]

**Recovering GRUB Manually**

 Before you can undertake the next step, it's important that you understand how GRUB identifies partitions. 
To GRUB, numbers begin with 0, and letters are expressed numerically, also beginning with 0. 
For example, /dev/hda1 is "hd0,0" to GRUB. Similarly, /dev/hdb3 is "hd1,2". 
**Note**: The "root" line must point to the location of your /boot/ partition if you have one. If you do not have one, point it at your / partition. 
sudo /sbin/grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit 
**Configuring the GRUB Menu**

 **Note**: This step does not need to be done if you're just trying to recover your MBR. Installing Windows will not alter the contents of your existing menu.lst, so if everything was working right before, everything will continue to work right now, and you can restart your computer. 
Open the GRUB menu file, /boot/grub/menu.lst, with your favourite text editor. An example follows. 
sudo nano /boot/grub/menu.lst**Note**: Your menu.lst file is used to control the operating systems GRUB displays on startup, as well as its visual appearance. This howto will only explain how to get your operating systems to boot; it will not tell you how to make your bootloader pretty. 
A sample menu.lst, stripped of unnecessary comments, appears below. It is based on the /dev/hda3 and /dev/hda4 example above, and assumes Windows resides at /dev/hda1. 
timeout 5 #The number of seconds GRUB should wait before booting an OS
default 0 #The entry which should be booted by default
fallback 1 #The entry which should be booted in the event of the first one failing

title  Ubuntu, 2.6.10 #A 32-bit Ubuntu entry
#This (or something like it) should be in your configuration
root   (hd0,2)
initrd /initrd.img-2.6.10-5-386
kernel /vmlinuz-2.6.10-5-386 root=/dev/hda4

title  Ubuntu, 2.6.10 #Another 32-bit Ubuntu entry
#This is an example of an Ubuntu entry which does not have a separate /boot/ partition
#(it is provided only as an alternate to the example above -- do not use them together)
root   (hd0,2)
initrd /boot/initrd.img-2.6.10-5-386
kernel /boot/vmlinuz-2.6.10-5-386

title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1And that's it. Save and close the file, then reboot and try out the entries.

---

### Post by ncalvin on 2009-06-08
That makes no sense to me. I don't know what I'm supposed to read, or what I'm supposed to code. And "sudo /sbin/grub" gives me command not found.

---

### Post by lifsuchy on 2009-09-30
sudo grub

This should put you into a Grub Menu which is what he was trying to get you to do.

The "root (hd0,1)"  points to where your grub is currently installed.  The 0 represents which hard drive you are point to (0 for first hard drive, 1 for second, etc) and the 1 represent which partition.

The "setup (hd0)"  is a command that is telling your system to install the grub menu into your first hard drive, or booting disc.  

This is a general quick fix way to get grub working again if you installed a dual boot system with windows.  That way your system will open a grub boot menu instead of using the Xp bootloader.

As posted above you will have to edit your grub menu.lst file and add a Windows XP entry so that you have it as an option to boot.

---

