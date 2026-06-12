---
title: "Getting GRUB to work again"
date: 2008-11-09
forum: General Help
---

### Post by Horomancer on 2008-11-09
I've recently made a Dual boot system composed of XP and Hardy. Things were great as I installed Hardy after XP (each on their own seperate HDs) until that is I had to do some work on XP using the install disk.
Now the computer will automatically boot into XP from shutdown and I don't know how to get back into Hardy.
I want to avoid reinstalling Hardy, since going through the setup and tweaking can be a hassle. Is their a way to get GRUB back in place as the boot loader?

---

### Post by caljohnsmith on 2008-11-09
OK, how about booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should reinstall Grub to your MBR and let you boot Hardy again, and if you had an entry for Windows in your Grub menu, you should be able to boot that too. If not, let me know. :)

---

### Post by geirha on 2008-11-09
The wiki has a page about it btw [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Horomancer on 2008-11-09
I booted from my live cd and ran the commands you had listed in the terminal.
It spit back the numbers (hd1,0)
I used these for the 'root' and 'setup' command and it seems everything went well, but when i restarte my comp I was kicked straight into XP

---

### Post by caljohnsmith on 2008-11-09
> **Horomancer said:**
> I booted from my live cd and ran the commands you had listed in the terminal.
It spit back the numbers (hd1,0)
I used these for the 'root' and 'setup' command and it seems everything went well, but when i restarte my comp I was kicked straight into XP
So did you use "root (hd1,0)" and "setup (hd1)"? If so, Grub should be properly installed to your sdb drive. If you are still booting Windows on start up, that's an indication you simply need to go into your BIOS and change the boot order so that the sdb drive boots first. Once you can boot the sdb drive, you should get the Grub menu. There's a good chance though that booting the OSes from the Grub menu will result in an error, but that's easy to fix. See if you can get the Grub menu first and we can work from there, otherwise let me know if you run into problems.

---

### Post by Horomancer on 2008-11-09
I ran the commands again to make sure i punched in the values correctly. I didn't get an error message but i still can't get GRUB to work. I've tried booting from both my HDs with the same result of being immedatly booted into Windows.

I think I'll try the Overwitting XP bootloader from the above link.

Using the overwitting XP bootloader walkthrough- would I run sudo grub-install on /dev/hda which is the first hard drive and the with XP installed, or on /dev/hdb?

---

### Post by caljohnsmith on 2008-11-09
OK, how about posting the following:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by Horomancer on 2008-11-09
Results of sudo fdisk -lu

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   195350399    97675168+   7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6d7f6d7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    25430894    12715416   83  Linux
/dev/hdb2        25430895    31294619     2931862+  82  Linux swap / Solaris
/dev/hdb3        31294620   117226304    42965842+  83  Linux


root@ubuntu:~# sudo dd if=/dev/hda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
root@ubuntu:~# sudo dd if=/dev/hdb1 count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
root@ubuntu:~# sudo dd if=/dev/hdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 


root@ubuntu:~# sudo dd if=/dev/hdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002

these are the read outs from the commands you gave.

---

### Post by caljohnsmith on 2008-11-09
OK, I see what could be preventing you from booting the hdb drive; some BIOSes will refuse to boot a drive that doesn't have one of its partitions marked as bootable, because the BIOS assumes it is then just a data drive. So to mark one of your hdb partitions as bootable, just do:
```
sudo fdisk /dev/hdb
```
"a" to toggle to boot flag, "1" for the partition, "w" to write the change, and "q" to quit fdisk. Then reboot, make sure BIOS is set to boot hdb first, and let me know if that gets you to the Grub menu at least.

---

### Post by Horomancer on 2008-11-09
root@ubuntu:~# sudo fdisk /dev/hdb

The number of cylinders for this disk is set to 7297.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): a
Partition number (1-4): 1

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
root@ubuntu:~# q
-bash: q: command not found
root@ubuntu:~# 

going to try and reboot now

Edit- I have just tried rebooting. Grub did not run and I went straight into XP like before.

---

### Post by psusi on 2008-11-09
You always setup (hd0) since that is the drive the bios boots from.

---

### Post by caljohnsmith on 2008-11-09
OK, how about checking your boot flag on hdb1 with:
```
sudo fdisk -l
```
If that shows an asterisk next to hdb1, and you are still not able to boot your hdb drive, then you might not have any choice but to install Grub to your Windows drive as psusi is suggesting. The disadvantage of that is your drives will be dependent on each other, i.e. if anything happens to either of them, you most likely won't be able to boot either Windows or Ubuntu. So although it is not as ideal as booting your hdb drive directly, at least you should be able to boot both OSes once you get Grub configured properly. To install Grub to your Windows drive MBR, just do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd0)
grub> quit

```
Reboot, and you should at least get a Grub menu on start up. Again, choosing the OSes from the menu may or may not work, but that's usually easy to fix. Let me know how it goes.

---

### Post by psusi on 2008-11-09
The boot flag only has meaning to the Windows MBR boot code, so it doesn't matter.

---

### Post by caljohnsmith on 2008-11-09
> **psusi said:**
> The boot flag only has meaning to the Windows MBR boot code, so it doesn't matter.
That's not true; some BIOSes will refuse to boot a drive that doesn't have one partition flagged as bootable. I have used computers where that is the case, and if you search the forums, you will see there are others who have run into the same problem.

---

### Post by Horomancer on 2008-11-09
OK i ran the grub commands again like you said and now grub works.
New problem-
There use to only be 3 linux boot options  in GRUB. Now there are 5
Normally I can choose from defualt Ubuntu, Safe mode, or memtest. Now there are what appear to be 2 linux sets (normal and safe mode) for two different kernels. It's late noww, but I'll post the full option list in the morning.

Thanks for all your help

---

### Post by psusi on 2008-11-10
> **caljohnsmith said:**
> That's not true; some BIOSes will refuse to boot a drive that doesn't have one partition flagged as bootable. I have used computers where that is the case, and if you search the forums, you will see there are others who have run into the same problem.

That's weird.  The bios is only supposed to check if the first word is 55AA, and if it is, execute it.

---

### Post by Horomancer on 2008-11-10
OK so when GRUB pops up it gives me the following choices-

Ubuntu 8.04.1 kernel 2.6.24-21 generic
Ubuntu 8.04.1 kernel 2.6.24-21 generic (safe mode)
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic (safe mode)
Ubuntu 8.04.1 kernel memtest
Windows XP

Currentl I'm booted in the top selection. I have no clue what the different kernels mean.

---

### Post by caljohnsmith on 2008-11-10
I think it is always good to have at least two kernels to choose from in your Grub menu; if for some reason you can't boot the most current kernel due to updates or something, then there's a chance the older kernel will still work. Hence I would recommend keeping all those boot options in your Grub menu, but it's up to you. If you decide to get rid of any of those options, just open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then you can delete the kernel entries in that file. Note that will just delete the option to boot the entry from the Grub menu, but you will still have the boot files in your /boot directory. So if you actually want to get rid of a kernel, you would have to use Synaptic to uninstall it. 

Anyway, glad you are at least able to boot into Ubuntu OK now. :)

---

### Post by Horomancer on 2008-11-11
Thanks for all your help. I'll keep those boot options since they aren't doing any harm as is.

---

