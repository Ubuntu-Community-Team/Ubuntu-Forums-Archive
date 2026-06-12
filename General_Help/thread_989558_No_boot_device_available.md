---
title: "No boot device available?"
date: 2008-11-21
forum: General Help
---

### Post by alka5eltzer on 2008-11-21
Hi all,

I have a 3 mth old Dell XPS 630i quad core PC.

I decided to install Ubuntu as a dual boot with my original Dell Vista Premium install.

I have - 2x 500Gb and 1x160Gb Seagate drives. I installed the 160Gb drive a month back and was uing it with Vista to store folders etc... no os is installed on it.

The 2 500Gb's were installed by Dell, the Vista OS and recover were installed on them.

So... here it is: :-({|=

I ran the Ubuntu install CD and told it to use the 160Gb drive to install Ubuntu.

The install went OK, I restarted the PC and got Grub error 21?

I messed about a bit... and now I'm getting "No boot device available"?

I've made sure all my boot prioritys are ok.

I really want to get Vista Back....soo....

I started the Vista recovey environment and ran Bootrec.exe.. long story short... nothings really seeing my C: drive... I tried replacing my MBR but it didn't work.

I'll be soo greatful if anyone have any ideas? :cry:

Thaks loads,

Shay
Derry, Ireland ;-)

PS: Next i'm gona try and run this to see if it helps: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by LateNiteTV on 2008-11-21
completely off topic, but i have half my family in derry!! lol. yeah. thats all. good luck with ur problem.

---

### Post by caljohnsmith on 2008-11-21
How about booting your Live CD, opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like right now.

---

### Post by alka5eltzer on 2008-11-21
> **LateNiteTV said:**
> completely off topic, but i have half my family in derry!! lol. yeah. thats all. good luck with ur problem.

Haa... t'is a small world lol ;)

---

### Post by alka5eltzer on 2008-11-22
> **caljohnsmith said:**
> How about booting your Live CD, opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like right now.

Hi John,

Thanks for your help & time... much appreciated.

I ran the Live CD and i've done what you've asked.. here's what it spit out... is it OK?:

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb028a7c6
Device Boot Start End Blocks Id System
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcacc504a
Device Boot Start End Blocks Id System
/dev/sdc1 63 9108854 4554396 83 Linux
/dev/sdc2 9108855 312496379 151693762+ 5 Extended
/dev/sdc5 299724768 312496379 6385806 82 Linux swap / Solaris
/dev/sdc6 9108981 287836604 139363812 83 Linux
/dev/sdc7 287836668 299724704 5944018+ 82 Linux swap / Solaris
Partition table entries are not in disk order
Disk /dev/sdh: 255 MB, 255590400 bytes
128 heads, 4 sectors/track, 975 cylinders, total 499200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67b1d1b5
Device Boot Start End Blocks Id System
/dev/sdh1 4 474623 237310 b W95 FAT32
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating
system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating
system"
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating
system"
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating
system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating
system"
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
0000
ubuntu@ubuntu:~$
```

Thanks again,
Shay

---

### Post by caljohnsmith on 2008-11-22
OK, one thing I see that could be an issue is that your Ubuntu sdc drive does not have a boot flag set on any of the partitions; although Grub does not care about whether the boot flag is set on a partition in order to boot it, there are some BIOSes that will refuse to boot a drive that doesn't have one partition flagged as bootable, because the BIOS then assumes the drive is for data only. That would most likely explain your "no boot device available" error. 

The other problem I see is that your Ubuntu sdc drive does not currently have Grub installed to its MBR, so probably what happened was that Grub was installed to the MBR of your sda drive when you installed Ubuntu, which is the default; that would explain your Grub error 21, because Grub in the MBR of sda was most likely pointing to (hd2) or the third drive in the BIOS boot order, and probably your Ubuntu sdc drive is actually second in the BIOS boot order since it appears that sda and sdb are some sort of RAID setup. So is that true, are sda and sdb set up as a RAID array? Or did I get that completely wrong? 

Anyway, fixing your problem might turn out to be easy; how about first setting the boot flag on your sdc1 partition by doing:
```
sudo fdisk /dev/sdc
```
Press "a", then "1" for the partition, then "w" to write the change, and finally "q" to quit. After that, do the following to install Grub to the MBR of sdc:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, and it should be either (hd2,0) or (hd2,5); but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd2)
grub> quit
```
Then reboot, set your BIOS to boot the sdc drive, and then you should at least get a Grub menu on start up if all goes well (or the "Press ESC to see menu" message). If you installed Intrepid and not a previous version of Ubuntu, probably Ubuntu will boot just fine from the Grub menu, but if not, let me know the error and we can work from there. Or let me know if you run into any other problems. :)

---

### Post by alka5eltzer on 2008-11-22
Hi there,

I did the above... but it still showing the "No boot device available"...

In my BIOS the only options I have in the Hard Disk priority page are:

1. SCSI-0  :  ID 01 HVIDIA STRIPE 931
2. Bootable Add-in Cards

In my IDE/SATA Configuration page I have:

SATA-0 [ST3500620AS]  *"This is 500GB drive 1"*
SATA-1 [ST3500620AS]  *"This is 500GB drive 2"*
SATA-2 [PLDS DVD+/-RW] *This is my DVD RW drive*
SATA-3 [ST3160815AS]  *"This is 160GB drive"*

Thanks

---

### Post by caljohnsmith on 2008-11-22
So you can't set your BIOS to boot the sdc drive? Also, do you know if sda and sdb are configured in some sort of RAID setup? When you had Vista working, did Vista see your two 500 GB drives as only one drive, or were they separate? How about posting the full output of the following:
```
sudo fdisk -lu
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```

---

### Post by alka5eltzer on 2008-11-22
Yes.. they are in a RAID setup and when vista was inatalled it saw the 2 500Gbs as one drive.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb028a7c6
Device Boot Start End Blocks Id System
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcacc504a
Device Boot Start End Blocks Id System
/dev/sdc1 * 63 9108854 4554396 83 Linux
/dev/sdc2 9108855 312496379 151693762+ 5 Extended
/dev/sdc5 299724768 312496379 6385806 82 Linux swap / Solaris
/dev/sdc6 9108981 287836604 139363812 83 Linux
/dev/sdc7 287836668 299724704 5944018+ 82 Linux swap / Solaris
Partition table entries are not in disk order
Disk /dev/sdh: 255 MB, 255590400 bytes
128 heads, 4 sectors/track, 975 cylinders, total 499200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67b1d1b5
Device Boot Start End Blocks Id System
/dev/sdh1 4 474623 237310 b W95 FAT32
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating
system"
GRUB
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff05
ubuntu@ubuntu:~$
```

---

### Post by caljohnsmith on 2008-11-22
Do you have an option on start up to press F10/F12 or some key like that to specify which drive you want to boot from (not the same as going in your BIOS and changing the boot order)? Most modern BIOSes have that feature now I think. At least the good news is it looks like Grub is properly installed to the MBR of sdc, and also sdc1 is marked as bootable, so that procedure must have gone fine. According to those previous "dd" commands you ran, your sda drive has a Windows MBR, so the drive should be bootable, or at least give a Windows type error when booted; but a "no boot device available" error is from your BIOS, so your BIOS is not even trying to boot the sda/sdb drives I think. 

Since you can't boot your sdc drive, I think about the only thing you can do concentrate solely on getting Vista booting again, and then you can add Ubuntu to Vista's boot menu. When you said "I started the Vista recovey environment", did you boot a Vista recovery partition on sda/sdb, or do you have a Vista Install CD? If you don't have a Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"); I would recommend trying the "Vista Repair" option from the CD and see how far you get. Let me know exactly what errors you might get when you try it.

---

### Post by alka5eltzer on 2008-11-22
> **caljohnsmith said:**
> Do you have an option on start up to press F10/F12 or some key like that to specify which drive you want to boot from (not the same as going in your BIOS and changing the boot order)? Most modern BIOSes have that feature now I think. At least the good news is it looks like Grub is properly installed to the MBR of sdc, and also sdc1 is marked as bootable, so that procedure must have gone fine. According to those previous "dd" commands you ran, your sda drive has a Windows MBR, so the drive should be bootable, or at least give a Windows type error when booted; but a "no boot device available" error is from your BIOS, so your BIOS is not even trying to boot the sda/sdb drives I think. 

Since you can't boot your sdc drive, I think about the only thing you can do concentrate solely on getting Vista booting again, and then you can add Ubuntu to Vista's boot menu. When you said "I started the Vista recovery environment", did you boot a Vista recovery partition on sda/sdb, or do you have a Vista Install CD? If you don't have a Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"); I would recommend trying the "Vista Repair" option from the CD and see how far you get. Let me know exactly what errors you might get when you try it.

Hi John,

I think I've worked out how to get it to boot but again... it booting nothing.

There seems to be 2 RAID arrays. One is the 2x500Gb drives and the other is the 160Gb drive.

What makes this confusing and what was maybe the problem way at the start was that you can set the RAID to boot a certain array, then the BIOS must be set to the same.
So what I think happened at the start was that the BIOS and RAID weren't set the same.

Soo... knowing this.. i reinstalled Ubuntu on to the entire 160Gb drive (sdc), I set the RIAD and Bios both to boot of this volume and when it boots... it just sits there with a flashing courser... nothing else on screen?

I wanted to see if the windows install CD would see the 3x500Gb drive and it does, even tho Ubuntu - when running the lives CD doesn't.
Windows see's the 2x500Gb drives as "Disk 0 unallocated space" with 100% free space.

It shows the 160Gb drive as "Disk 1 Partition 1" but it won't allow me to install windows on this drive as it not NTFS (not that I want to do that at the min lol).

Any who... is there any way I can pull my files/data off drive 1 (2x500Gb)... or can I tell it there's actually stuff on the disk?

Thanks loads,
Shay

---

### Post by caljohnsmith on 2008-11-22
Is there some way you can turn off your RAID hardware (maybe in BIOS) so that sda and sdb become separate drives? If you can do that, then probably the Ubuntu Live CD will be able to mount and read your NTFS partitions on those drives just fine, and you can back everything up. It looks like the crux of your problem right now is how you have your drives improperly RAIDed together, because neither the Ubuntu or the Windows CD can access those drives. Bottom line is, I think you either have to get the RAID working so that you can access those drives, or simply disable RAID to make them separate drives. Good luck and keep me posted.

---

### Post by heraldo on 2009-06-14
Hi,

had a Grub Error 17 simply after re-installing ubuntu 9.04 on /dev/sdc (sda and sdb are both software raid1). No windows, this comp has always been linux, so no dual-booting issues.
Anyhow, I think grub got confused to from which drive to boot. "fdisk -l" said /dev/sda was boot. But I have done exactly what you have told in [http://ubuntuforums.org/showpost.php?p=6229483&postcount=6](http://ubuntuforums.org/showpost.php?p=6229483&postcount=6) and it worked!

Thanks.

---

