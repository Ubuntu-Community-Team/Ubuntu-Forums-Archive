---
title: "ext4 partition became unallocated after installing win 7"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by abboss on 2009-05-10
Hello everyone, I am a newbie who is migrating to Linux from windows and now having troubles with ext4. And a new member of forum also! :)
 I have been using dual-boot (with Grub) Jaunty with Windows 7 both in separate partitions ext4(20GB) and ntfs(100GB). Two days ago I installed new Windows 7 RC, during installation I divided ntfs partition into two partitions and installed Win 7 RC to one of them. Without touching other ext4 & swap Linux partitions. Usually Windows 7 deletes grub and installs Vista loader. When you switch it on it boots directly to windows. To install grub and access to Linux again I used to reinstall Ubuntu with live CD, marking the same partition as "/" without formatting, it keeps all the files and settings when you import them. But this time it did not work out.... :( Jaunty installation cd showed ext4 partition as unallocated and I had to install it to the third partition I created when installing windows, formatting it as ext4, without touching old ext4 part again. Now both Windows 7 and Jaunty showing the old ext4 Linux partition as UNALLOCATED. It was always ok with ext3 and I am being lil bit conservative these days :P
 All of my files were there :(
Please help me to get my data out from there.

Thanks beforehand.

---

### Post by lovinglinux on 2009-05-10
> **abboss said:**
> To install grub and access to Linux again I used to reinstall Ubuntu with live CD, marking the same partition as "/" without formatting, it keeps all the files and settings when you import them. But this time it did not work out.... :( 

I don't think this is the best method to restore Grub. I think you accidentally deleted the partition containing Ubuntu. Next time follow these.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


> **abboss said:**
>  All of my files were there :(
Please help me to get my data out from there.

Do not format it until you get your data back. I'm not sure if a deleted partition would allow to recover files, but if you format then your chances will drop.

There are some recovery programs like Photorec, but I never used it.

Try [these](http://www.google.com/search?q=recover+files+deleted+partition+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0)

---

### Post by abboss on 2009-05-10
Yes, I didn't know this:
> [https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows)
it seems better. Thanks.

I can't stop thinking ab my data...:o
Maybe I have to wait for developers upgrade some software to work with ext4 issues :rolleyes:

---

### Post by caljohnsmith on 2009-05-10
How about posting the following commands so we can get a better idea how Ubuntu sees your partitions:
```
sudo fdisk -lu
sudo sfdisk -d
```

John

---

### Post by abboss on 2009-05-10
Thank you for attention John ;
here is it

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc2eba2e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848    72706047    36249600    7  HPFS/NTFS
/dev/sda3        72706048   177692671    52493312   83  Linux
/dev/sda4       230468490   234436544     1984027+   5  Extended
/dev/sda5       230484555   234436544     1975995   82  Linux swap / Solaris
abboss@abboss-laptop:~$ 

```

---

### Post by caljohnsmith on 2009-05-10
According to fdisk, you do have a ~25 GiB chunk of unused disk space after sda3. Based on what you've said so far, I think there's a good chance you could use "testdisk" to recover your lost ext4 partition; to use testdisk, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions and the lost ext4 partition. We can work from there if you want.

John

---

### Post by abboss on 2009-05-10
> According to fdisk, you do have a ~25 GiB chunk of unused disk space after sda3. Based on what you've said so far, I think there's a good chance you could use "testdisk" to recover your lost ext4 partition; to use testdisk, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
 	Code:
 	cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static 
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while.

Thank you John, changing
> sudo testdisk-6.11/linux/testdisk_static

to ```
sudo testdisk-6.11.1/linux/testdisk_static
```

it worked, now it is searching...
 I'll post the results when it finishes.

---

### Post by abboss on 2009-05-10
So, here is the search results:
```

TestDisk 6.11.1, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 11060 254 63  177694902
D HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
D HPFS - NTFS             12 223 20  4525 189 16   72499200
D HPFS - NTFS           2632   1  2 14592 254 63  192153401
D Linux                 4525 189 17 11060 218 38  104986624
D Linux                 7678 128  3 14213 157 24  104986624
D Linux                 7679   3  5 14214  32 26  104986624
D Linux                 7683  23 21 14218  52 42  104986624
D Linux                 7685 228 32 14221   2 53  104986624
D Linux                 7686   6  1 14221  35 22  104986624
D Linux                 7686 103 34 14221 132 55  104986624
D Linux                 7686 233 36 14222   7 57  104986624
D Linux                 7688   0  1 14223  29 22  104986624
D Linux                 7690  91 18 14225 120 39  104986624
D Linux                11061   2  1 14345 254 56   52773392
D Linux Swap           14347   0  1 14592 254 41    3951968






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 27 GB / 25 GiB

 
```

---

### Post by abboss on 2009-05-11
Thank you very much John, program worked well, after analyzing I browsed using keys "p" and "q" I found all my data safe and then easily copied them. :P
I my data rescued now :)
I will be careful next time. Thank you brother.

---

### Post by lovinglinux on 2009-05-11
> **abboss said:**
> Thank you very much John, program worked well, after analyzing I browsed using keys "p" and "q" I found all my data safe and then easily copied them. :P
I my data rescued now :)
I will be careful next time. Thank you brother.

That's really nice!

I'm bookmarking this thread for future reference.

---

### Post by lpd on 2009-07-26
Something similar happened to me tonight. Had reserved 4 GB for Win/other OS and figured I should install something.. however the install messed up the MBR and I tried to fix this using the wrong tool... My Ubuntu 9.04 installation was on ext4fs. 

So.. I used Smart FDISK 2.04 (I think).. and I didn't think... chose to fix MBR and install something.. gah! And I am an experienced IT pro... ha! back to school for me. 

After that exercise in stupidity the hard drive appears to be empty, E-M-P-T-Y. To my grief. And I had only backed up 80-90% and the email system was backed weeks ago. _I_ should know better of course. What have we learned from this? NEVER make huge system changes WITHOUT a VERY VERY recent backup.

I am now trying TestDisk... It has found the EXT4 partition, it is marked as deleted. I shall now try to recover /home and some system files... btw, there's a more recent release of TestDisk. Vistit [http://www.cgsecurity.org](http://www.cgsecurity.org). Thanks to John for the tip.

Update: Using Testdisk I backed up some of the most important files from the disappeard/deleted ext4 partition. However, Testdisk was unable to copy large files (2-4 GB), which resultet in the error "Killed" and Testdisk exits. I studied Testdisk's functionality and found out that it can write a new partition table, I was unsure of how my partition table looked like before the crash, but sometimes you just have to guess.. :) I wrote the new partition table and restarted the computer. Using Ubuntu Live 9.04 from a flash drive I continued, rebooted into the flash drive and then checked the partitioning on /dev/sda using fdisk -lu. It looked nice, after that I reinstalled grub and rebooted once again. This messege is written from the dead system. BTW, I was unsure if Testdisk could handle ext4 partitions, it is not mentioned in the documentation and specs, but it worked. I guess the difference between ext3 and ext4 is not that big. I am now going to send some money to Christophe Grenier, Testdisk is worth a whole lot to me, and I sure want him to continue to develope it.

---

### Post by Darkmoon_UK on 2009-10-22
I have to report the same; installed Windows7 on the same drive as contains my ext4 /home partition. When I returned to booting Ubuntu, it failed and I discovered the ext4 partition had been deleted (gparted reports unallocated space).

I am sure I didn't accidently delete it during the Windows7 partition setup, so what has gone on here? 2 other NTFS partitions and a Linux Swap partition were unaffected.

I don't think it should make any difference, but its worth noting this drive is a RAID0 setup on a Sil3132 controller.

---

### Post by sevcsik on 2009-10-26
I can confirm this too. After win7 install (i had a previous windows partition, so I only used the installer to format it), my home ext4 partition lost. Fortunately i could restore it with testdisk, thanks to this thread :)

Looks like it's a win7 installer bug. pretty annoying one, though... :mad:

---

### Post by amzertech on 2009-10-27
Check this out     [http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)

---

### Post by meho_r on 2009-10-27
> **sevcsik said:**
> 

...Looks like it's a win7 installer bug. pretty annoying one, though... :mad:

No, it's not a bug, it's a feature :P

---

### Post by hvymtlsteve on 2009-11-01
I had a similar thing just happen today, except with Windows Vista and not Windows 7.

Windows Vista came on this laptop, and the first thing I did was halve the size of the OS partition to install Ubuntu. 
I suspect the issue lies with the fact that Vista had a separate Data partition set aside as well, which I tried to delete from within Windows first, but it was taking too long so I decided to wipe it out from gparted on the Ubuntu install instead, and use the space for my home partition. 

I didn't know if that was gonna screw with the Win install, but had a hunch that it might.. didn't boot into Windows though, for a whole month and a half, until today, when I wanted to try out a tool that I didn't feel like messing with in Wine just yet.

When I was done I tried booting back into Ubuntu, only to find that my home partition was not found.. gparted on the live CD shows that the partition is now unallocated space. What a mess. :mad:

I suppose I will try to get my data back, and then maybe just do a clean install of Karmic.

---

### Post by e.farid on 2010-01-21
Hi all,
It also happened to me today !
The only difference in my case that it happened when i was installing windows xp !

I'll try to recover my data today and hope it works...

---

### Post by Rob2687 on 2010-09-22
I had the same problem as OP. I had a new install of Windows 7 on the first partition and Ubuntu on the extended partition. After the new Windows install the Linux partitions were set as unallocated after installing Windows.

Testdisk was able to recover the Linux partitions but it wrecked the Windows 7 partition. 

So I am kind of a stuck situation here. If I install Windows again and the Linux partition goes unallocated. If I repair the Linux partitions I lose the Windows partition.

---

### Post by greylander on 2010-11-05
I have been hit with this too.  It definitely seems to be something Win 7 installer does, as I have done nothing with the partitions or with grub since the install.  All logical partitions within my ext4 extended partition are now "unallocated space".  Oddly, the Linux swap partition (also a logical inside the ext4) survived.

Gonna have to try this testdisk... sound like results have been positive here.

---

### Post by wilee-nilee on 2010-11-05
> **greylander said:**
> I have been hit with this too.  It definitely seems to be something Win 7 installer does, as I have done nothing with the partitions or with grub since the install.  All logical partitions within my ext4 extended partition are now "unallocated space".  Oddly, the Linux swap partition (also a logical inside the ext4) survived.

Gonna have to try this testdisk... sound like results have been positive here.

This happens if you don't build the ntfs partition ahead of time. If you have a dual boot W7, Linux and want to reinstall W7 or any MS really, build the partition first, best probably with gparted. With W7 if you let it build the partition it makes two, a 200Mib boot and the OS partition. This has made my Linux go unallocated twice before I figured this out.

I have everything backed up so when this happened I LOL at my own ineptness.;)

---

### Post by greylander on 2010-11-05
wilee -- I may just be remembering wrong, but I think that I did build the NTFS partition with gparted before installing windows... but it is possible that I just made space for it and let W7 do its own thing.

Seems like W7 overwrites the partition table and conveniently leaves out the partitions containing OS's it doesn't like.  :P

---

### Post by wilee-nilee on 2010-11-05
> **greylander said:**
> wilee -- I may just be remembering wrong, but I think that I did build the NTFS partition with gparted before installing windows... but it is possible that I just made space for it and let W7 do its own thing.

Seems like W7 overwrites the partition table and conveniently leaves out the partitions containing OS's it doesn't like.  :P

If you have 200 MIB boot partition and the main W7 partition usually called C then you didn't format it ahead of time. When you pre-format the ntfs W7 installs to one partition, if you are using a straight install DVD.

---

### Post by VraiChevalier on 2010-11-06
This same problem happened to me on an Acer Aspire One D250 dual booting Windows 7 Starter and Ubuntu 10.04. Only I had **_not_** done anything with my Windows partitions. I had just installed the LXDE desktop, didn't like it, and so tried the KDE desktop (for some inexplicable reason I decided to mess with a perfectly usable system - sigh). After logging out from KDE and trying to log back in much to my dismay my Ubuntu / partition was gone. Or, more accurately, "unallocated". Bummer. My swap and NTFS were still there, intact. I had thought the problem to be with the ext4 file system. Wish I had found this thread before re-installing.:confused:

---

### Post by Amente on 2011-10-30
I faced the same problem. And the solution given here worked.....Thanks.....You saved my soul.......

---

### Post by oldos2er on 2011-10-30
Back to sleep. Please don't bump old threads.

---

