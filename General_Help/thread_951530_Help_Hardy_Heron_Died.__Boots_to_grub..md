---
title: "Help: Hardy Heron Died.  Boots to grub."
date: 2008-10-18
forum: General Help
---

### Post by yubrew on 2008-10-18
Hi, I am new to Ubuntu.  The power went out in my house while I was sleeping, and Hardy Heron was on.  I woke up to a laptop with 0% power.  When I powered the laptop on again, it went directly to a grub commandline screen.  After restarting, it continues to go to grub commandline.

Between the time I select Ubuntu and the grub commandline screen, there are no indications that there are any errors.

I tried searching through this thread, but could not find any similar problems to mine.  I don't know my way around grub at all.

Here are the specs: 
Wubi 8.04.1 - Windows Vista/Ubuntu 8.04 dual booting
Acer Aspire 4520
AMD Athlon 64x2
4 GB DDR2 ram

---

### Post by yubrew on 2008-10-18
I now see there's a thread very similar to this one:
[http://ubuntuforums.org/showthread.php?t=951523](http://ubuntuforums.org/showthread.php?t=951523)

> **yubrew said:**
> Hi, I am new to Ubuntu.  The power went out in my house while I was sleeping, and Hardy Heron was on.  I woke up to a laptop with 0% power.  When I powered the laptop on again, it went directly to a grub commandline screen.  After restarting, it continues to go to grub commandline.

Between the time I select Ubuntu and the grub commandline screen, there are no indications that there are any errors.

I tried searching through this thread, but could not find any similar problems to mine.  I don't know my way around grub at all.

Here are the specs: 
Wubi 8.04.1 - Windows Vista/Ubuntu 8.04 dual booting
Acer Aspire 4520
AMD Athlon 64x2
4 GB DDR2 ram

---

### Post by caljohnsmith on 2008-10-18
I think the first thing I would do if I were in your predicament would be to do file system check on your Ubuntu partition and make sure it is OK. Please post:
```
sudo fdisk -lu
```
And then for whichever partition is your Ubuntu partition (it should be type "linux" under the "system" heading), do:
```
sudo fsck -y /dev/sdaX
```
and replace sdaX with the Ubuntu partition. Let me know if that finds any errors, and if it changes anything when you reboot. :)

---

### Post by yubrew on 2008-10-18
Forgive me for my ignorance, but the computer does not recognize those commands from the Grub commandline.  Should I be entering this from a live CD terminal?

> **caljohnsmith said:**
> I think the first thing I would do if I were in your predicament would be to do file system check on your Ubuntu partition and make sure it is OK. Please post:
```
sudo fdisk -lu
```
And then for whichever partition is your Ubuntu partition (it should be type "linux" under the "system" heading), do:
```
sudo fsck -y /dev/sdaX
```
and replace sdaX with the Ubuntu partition. Let me know if that finds any errors, and if it changes anything when you reboot. :)

---

### Post by caljohnsmith on 2008-10-18
> **yubrew said:**
> Forgive me for my ignorance, but the computer does not recognize those commands from the Grub commandline.  Should I be entering this from a live CD terminal?
No problem, and yes, you should do those commands from a Live CD terminal. :)

---

### Post by yubrew on 2008-10-18
The "sudo fdisk -lu" prints out:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x689a676d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  27  Unknown
/dev/sda2   *    20467712   127723519    53627904    6  FAT16
/dev/sda3       127723520   234438655    53357568    7  HPFS/NTFS

I wasn't sure if it was sda2 or sda3.  I'm using Wubi.  The output of the command "sudo fsck -y /dev/sda3"

fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda3
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda2
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

---

### Post by TeXtonyx on 2008-10-18
Yes, you'll have to boot from the live cd to follow that approach.

I think that Windows users who are new to Ubuntu have the priority of
getting Vista/XP to work first. Better yet, don't let Ubuntu which drags
grub with it incapacitate Vista. Boot Vista and Ubuntu from the Vista
bootloader. Set up your grub menu.lst to boot Vista. If Vista should
fail you can boot Ubuntu from the Super Grub disk. I get the impression
that you can't boot either OS now. It doesn't have to be that way.
Install grub to the boot partition, not the MBR, step 7, Advanced, the
next time you reinstall Ubuntu. You will need a Vista install cd and
with bootrec, fixmbr and fixboot so you can repair your MBR. Some
laptops don't come with a install cd, they have recovery cds which
have no option to run bootrec. That is why it is an uninformed choice to 
install grub to the MBR when you dual boot; 60% of Ubuntu users dual boot. 

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)
Step 1 – Install GRUB on the Linux partition (outside of MBR)
Step 2 – Get a copy of Linux boot sector
a few more steps

This method is more manual than Easybcd, but also more educational. 
This example uses the dd command. It is easier to use free Bootpart and it will copy the 
512 bytes to C:\ This works the same way with XP except it writes to boot.ini rather than bcdedit

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
More emphasis on installing Ubuntu with pictures.
Step Five
"Now is the time to tell Ubuntu that we don't want GRUB installed
to the system bootloader. Instead, we're going to have Ubuntu install GRUB to its own 
partition, where EasyBCD can safely and easily read & interact with it, without too much 
hassle and absolutely no trouble."

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
Vista and ubuntu 8.04 with pictures.

---

### Post by caljohnsmith on 2008-10-18
OK, try doing this from the Live CD:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt/ubuntu/disks
```
Note "-l" is a lowercase L, not a one. If that shows a "root.disk" file, then proceed with:
```
sudo fsck -y /mnt/ubuntu/disks/root.disk
```
Please post the output of the above commands, and if you run into any problems, please also post:
```
ls -lR /mnt/ubuntu
```

---

### Post by TeXtonyx on 2008-10-18
I may have jumped the gun on the assumption that you couldn't boot
Vista, you didn't say that. I have never used wubi so I looked it up.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Cannot boot into Ubuntu

"Ubuntu cannot be booted if Windows has not been shut down cleanly, 
you have to clear the Windows filesystem from Windows (there is no 
chkdsk equivalent for Linux yet). If Wubi fails to start, boot into
windows, run chkdsk /r from windows on the same drive where you 
have installed Ubuntu, shutdown cleanly and then try to boot into 
Ubuntu again."

I did see [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk

which reminded me of "Code: sudo fsck -y /mnt/ubuntu/disks/root.disk"

TeX: The power outage caused the Windows file system to not shut
down cleanly. I've been unable to mount a Windows partition from
within Ubuntu when the Windows file system has not shut down
cleanly, and it doesn't have to be caused from a power outage.
A power outage once damaged several sectors on the hard drive.
I don't think it can hurt to try both wubiGuide suggestions.

---

