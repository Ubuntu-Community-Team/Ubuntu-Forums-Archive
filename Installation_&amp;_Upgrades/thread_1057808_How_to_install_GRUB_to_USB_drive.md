---
title: "How to install GRUB to USB drive"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by javaman1909 on 2009-02-02
I do some google search about this issue, but they only mentiona about install whole Ubuntu to USB drive. Then, how about only GRUB is installed in USB drive while Ubuntu is installed in internall HDD?

I have read an articles long ago, it mentioned about the solution that we can have both Linux distros and Windows installed on internal HDD, only GRUB is installed on thumb driver (or floppy disk). Then, when we want to boot to Linux distros, we simply plug the thumb drive in, GRUB will appear so that we can choose to boot to Linux, otherwise it will automatically boot to Windows. For example, if I have Windows, Ubuntu, BSD and Solaris installed on internal HDD. Only Windows boot loader is installed in MBR of the internall HDD. Then, I will have 3 different thumb drives which I name
them Ubuntu, BSD and Solaris respectively. They contain the GRUB configuration files of those Linux distros.

 If I want to boot to Windows, I simply power on my computer and do nothing, the Windows boot loader will load Windows. If I want to boot to Ubuntu (which I mention above, is installed on internal HDD), I power on my computer, plug in the Ubuntu drive, which contains Ubunu GRUB configuration files, the GRUB of Ubuntu will appear and let me choose to boot to Ubuntu.

This solution separates the GRUB config files to many medias, therefore GRUB of one Linux distro does not over flap another one Linux distro as well as Windows boot loader. Furthermore, we can re-install any OS that we want and do not need to worry about GRUB.  

Does anyone have any idea how we can do that

Thanks.

---

### Post by caljohnsmith on 2009-02-02
Yes, it is possible to do exactly what you want to do. How about first posting the output of:
```
sudo fdisk -lu
```
Please identify your partitions, and we can work from there if you want.

---

### Post by javaman1909 on 2009-02-02
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ef97ef9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102414374    51207156    7  HPFS/NTFS
/dev/sda3       102414375   625137344   261361485    5  Extended
/dev/sda5       102414438   204828749    51207156    7  HPFS/NTFS
/dev/sda6       204828813   409641434   102406311    7  HPFS/NTFS
/dev/sda7       409641498   457900694    24129598+   7  HPFS/NTFS
/dev/sda8       511059843   553005494    20972826   83  Linux
/dev/sda9       553005558   567351539     7172991    7  HPFS/NTFS
/dev/sda10      567351603   571560569     2104483+  82  Linux swap / Solaris
/dev/sda11      571560633   625137344    26788356    7  HPFS/NTFS

Disk /dev/sdb: 517 MB, 517341184 bytes
218 heads, 45 sectors/track, 103 cylinders, total 1010432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          45     1010429      505192+   b  W95 FAT32


sda is my internal HDD, sdb is my thumb drive.
sda1 contains Windows Vista.
sda8 contains Ubuntu (which start from /), this is only partition dedicated for Ubuntu.

Now, what I want is simply move the GRUB to sdb, so that each time when I plug in my thumb drive, the GRUB will be loaded, and I then boot to Ubunt. In contrast, if there is no thumb drive found during the POST, Windows will be loaded automatically.

Thank for your help.

---

### Post by caljohnsmith on 2009-02-02
OK, how about trying this:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,7)
grub> setup (hd0)
grub> quit
```
And please post the output of the commands before typing "quit". Then reboot, set your BIOS to boot the USB drive, and if all goes well you should get the Grub menu. If you are using Ubuntu Intrepid, you should be able to boot into Ubuntu, but if you have a previous Ubuntu version, we will probably have to tweak your Grub menu a little to get Ubuntu booting. But first let me know how far you get, and we can work from there.

---

### Post by javaman1909 on 2009-02-02
> grub> device (hd0) /dev/sdb

grub> device (hd1) /dev/sda

grub> root (hd1,7)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"...  20 sectors are embedded
.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+20 p (hd1,7)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> 


I am going to reboot now.
Hope it works.
Thanks

---

### Post by javaman1909 on 2009-02-02
It works, I can boot from USB drive now. After it boot to Ubuntu, can I unplug the USB drive?

I know how to modify /boog/grub/menu.lst, but in this case, where do I go to find the GRUB? on internal HDD or USB thumb drive (I cant find any config file on my USB drive). I want it auto boot to Ubuntu (no need to display menu) when I plug in USB drive.

Besides, I don't want to see GRUB when no USB found during POST, can I just use Vista Disk to boot to recovery console and use "fixmbr" to have Vista boot loader take part?

Last one, if I have one more Linux distro (eg FreeBSD), and I have one more USB thumb drive, do I do exactly the same as the 1st USB thumb drive?

Thanks so much for your consideration.

---

### Post by caljohnsmith on 2009-02-02
> **javaman1909 said:**
> It works, I can boot from USB drive now. After it boot to Ubuntu, can I unplug the USB drive?

Yes, as long as the USB drive is not mounted you should be fine.
> **javaman1909 said:**
> 
I know how to modify /boog/grub/menu.lst, but in this case, where do I go to find the GRUB? on internal HDD or USB thumb drive (I cant find any config file on my USB drive). I want it auto boot to Ubuntu (no need to display menu) when I plug in USB drive.

You can continue to use the FAT partition on your USB drive as usual, the only thing we did was install Grub to the MBR of your USB drive and configure Grub to look on your sda Vista/Ubuntu drive in the Ubuntu sda8 partition for its boot files. So if you want to modify the Grub menu you get when you boot the USB drive, you can just modify the menu.lst in your /boot/grub directory in sda8:
```
gksudo gedit /boot/grub/menu.lst
```
You can run the above command while you are in Ubuntu on sda8 to modify your menu.lst. 

> **javaman1909 said:**
> 
Besides, I don't want to see GRUB when no USB found during POST, can I just use Vista Disk to boot to recovery console and use "fixmbr" to have Vista boot loader take part?

Sure, now that you can boot Ubuntu from your USB stick, it is safe to restore a Windows MBR to your Vista/Ubuntu sda drive. If you use a Vista CD, the command is actually:
```
bootrec /fixmbr
```
> **javaman1909 said:**
> 
Last one, if I have one more Linux distro (eg FreeBSD), and I have one more USB thumb drive, do I do exactly the same as the 1st USB thumb drive?

Thanks so much for your consideration.
If you have or are going to install another Linux distro on sda, you could use a different USB stick to boot it, or you could simply add that distro as an option to boot in your Ubuntu's Grub menu. It's up to you. If you make a bootable USB stick for the new distro, you will need to modify "X" below:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root [COLOR="Blue"](hd1,X)[/COLOR]
grub> setup (hd0)
grub> quit
```
So "X" would be the partition the new distro is on, and remember that Grub's numbering begins with 0, not 1. Good luck and let me know how it goes.

---

