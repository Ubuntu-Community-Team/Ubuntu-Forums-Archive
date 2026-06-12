---
title: "Recovering grub with LVM encryption -- special considerations?"
date: 2008-11-19
forum: General Help
---

### Post by RichPowers on 2008-11-19
Hello,

My PC has two hard drives: one for Windows XP and one for an encrypted installation of Ubuntu 8.04. I reinstalled XP earlier and now I'm trying to recover grub so I can boot into Ubuntu again.

I installed Ubuntu 8.04 back in April and can't remember how I set it up, but it's worked flawlessly so I did something right :)

I attempted the grub recovery steps in [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to no avail. For example, I get the following:

```

grub> find /boot/grub/stage1

Error 15: File not found

```

Here is what I get when I run fdisk -l

```

/dev/sda1 ... HPFS/NTFS
/dev/sda2 ... W95 Ext'd (LBA)
/dev/sda5 ... W95 FAT16 (LBA)
/dev/sda6 ... W95 FAT16 (LBA)

/dev/sdb1 ... Linux
/dev/sdb2 ... Extended
/dev/sdb5 ... Linux

```

Because I setup LVM encryption with the alternate installer, do I need any sort of special steps to recover grub?

Thank you for your help.

---

### Post by louieb on 2008-11-19
You may have set up a separate /boot partition. at the grub> prompt try ```
find /grub/stage1
```

---

### Post by RichPowers on 2008-11-19
louie,

That command gets me past error 15, but now I run into the following problem:

```

grub> find /grub/stage1
(hd1,0)

grub> root (hd1)
grub> setup (hd1)

Error 17: Cannot mount selected partition

```

(I tried the same command only with (hd0) [by accident] and got the same results)

---

### Post by caljohnsmith on 2008-11-19
You should use the output of the find command for the "root" command like so:
```
grub> root (hd1,0)
grub> setup (hd1)

```
Also, the "setup (hd1)" installs Grub to the MBR of the sdb drive; that's ideal if you can boot the sdb drive on start up. If you can only boot the sda drive, you could instead use "setup (hd0)" to install Grub to the MBR of sda. Give that a shot and let us know how it goes.

---

### Post by RichPowers on 2008-11-19
caljohn:

Tried (hd1,0) and grub did its thing and said "success." I then quit my live disc session and rebooted...still no grub, went straight to WinXp.

I will now try "setup (hd0)" to see if that works.

---

### Post by caljohnsmith on 2008-11-19
> **RichPowers said:**
> caljohn:

Still no luck. After entering the correct output (hd1,0), grub did its thing and said "success." I then quit my live disc session and rebooted...still no grub, went straight to WinXp. But it looks like I'm getting closer to doing this right.
See my previous post; if you use "setup (hd1)", you'll need to set your BIOS to boot the Ubuntu sdb drive on start up; that's why you are still booting into Windows. If you have no way of changing your BIOS to boot your sdb drive, you can instead use "setup (hd0)" to install Grub to the MBR of your Windows sda drive, and that should work. :)

---

### Post by RichPowers on 2008-11-19
Okay, I switched the BIOS boot order and grub came up.

But nothing on the grub menu works :(

I get error 17s when I click on Ubuntu 8.04.1 ... generic or (recovery mode)

When I click on Windows XP Professional, it gives me Error 13: Invalid or unsupported executable format

Edit: Also the "generic (recovery mode)" pair is listed three times, for a total of six lines of Ubuntu operating systems...

---

### Post by caljohnsmith on 2008-11-19
OK, when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Also, change your Windows entry in the menu.lst to be:
```
title	   Windows XP Professional
rootnoverify      (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by RichPowers on 2008-11-19
caljohn, thank you so much for helping me fix grub and boot into Ubuntu and WinXP :KS

If I may bother you with one last thing:

I'm writing a how-to guide so that when I reinstall WinXP I can avoid some of these problems. Several wikis recommend saving grub to a floppy, but my PC lacks a floppy drive. Is a live CD session the only way for me to restore grub the next time? Is it safe to assume that the drive locations (hd0, Y) will remain the same?

PS: Can I delete the excess Ubuntu entries in menu.lst so that only one pair of generic/recovery mode options appears on startup?

---

### Post by caljohnsmith on 2008-11-19
> **RichPowers said:**
> caljohn, thank you so much for helping me fix grub and boot into Ubuntu and WinXP :KS

If I may bother you with one last thing:

I'm writing a how-to guide so that when I reinstall WinXP I can avoid some of these problems. Several wikis recommend saving grub to a floppy, but my PC lacks a floppy drive. Is a live CD session the only way for me to restore grub the next time? Is it safe to assume that the drive locations (hd0, Y) will remain the same?
As long as you can boot a Live CD, I can't think of any reason to save any Grub files or the Grub MBR to a floppy. And as long as you don't do any repartitioning, all the (hdX,Y) values shouldn't change. 
> **RichPowers said:**
> 
PS: Can I delete the excess Ubuntu entries in menu.lst so that only one pair of generic/recovery mode options appears on startup?
Sure, you can certainly do that if you want to clean up your Grub menu; keep in mind though that just deleting a Grub entry in your menu.lst won't delete any of the kernels in the /boot folder. It's always a good idea to have at least one older "backup" kernel listed in your Grub menu besides the newest kernel you are using in case you have problems with the latest kernel at some point. To uninstall any of the older kernels, you can use Synaptic to uninstall the following packages (for example the 2.6.24-16 version):
```
linux-headers-2.6.24-16-generic
linux-image-2.6.24-16-generic
linux-restricted-modules-2.6.24-16-generic
linux-ubuntu-modules-2.6.24-16-generic
```
By the way, did you end up running "setup (hd0)" at some point? If you did, you put Grub in the MBR of your Windows drive, and you won't be able to boot into Windows if anything happens to your Ubuntu drive; since you can boot the Ubuntu drive directly on start up, it would be good to restore a Windows MBR to your Windows drive in case you need to boot that drive should something happen to the Ubuntu drive. Let me know if you need a hand with that.

Anyway, cheers and have fun with Ubuntu. :)

---

