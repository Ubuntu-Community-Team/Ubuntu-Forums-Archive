---
title: "boot menu missing"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by Timmeh02 on 2009-08-09
I have successfully installed ubuntu 9.04 on my Dell Inspiron 6400 laptop.  I was happily downloading via transmission for several days.  For some reason the computer locked up when I was comparing two browsers at the same time.  I had Opera and Firefox open and the computer locked up.  I re-started the computer and now there is no longer the option on the bootup screen to select ubuntu beneath windows.  Ubuntu is not visible at all.  How do I recover the bootup menu option to select ubuntu.  

Cheers, Timmeh

---

### Post by gabry79Italy on 2009-08-09
try to boot from cd live ubuntu 9.04
terminal
sudo grub
find /boot/grub/stage1
the output will be like this: (hdx,y)
root (hdx,y)
setup (hd0)
quit
If the instructions above do not work, please post :
sudo fdisk -l

---

### Post by Timmeh02 on 2009-08-09
I have taken a screen shot of terminal which i am running from the live cd.  I'm not sure what to do from her though.  Thanks.

---

### Post by raymondh on 2009-08-09
> **Timmeh02 said:**
> I have taken a screen shot of terminal which i am running from the live cd.  I'm not sure what to do from her though.  Thanks.

If this is a non-wubi install, and from the instructions of gabry (above), enter one at a time the codes ....

find /boot/grub/stage1  *(which will produce a (hdX,Y) output*
root (hdX,Y)                   *(following the output from find)*
setup (hd0)
quit

Reboot.

If no joy, access terminal again, type and post back output of

```
fdisk -l
```

---

### Post by Acidwarlord on 2009-08-09
Hi..

i have a similar problem since today.
Hope its okay, if i use this thread too.

---=>
On the first hdd i have Win7 for testing, on the second i installed with the option for getting the boot menue between win/linux.

The problem is, that im only able to start from the first hdd(second only over extra bios boot menu !each time!)

Grub was installed on the second hdd and has the entry for Win7 but my pc only starts from first hdd.. so i need to install grub on the first hdd but its important for me, to keep the win7 loader and settings O.o so how i do it ?

Here's flist:
```
Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x97773bd1

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 endet nicht an einer Zylindergrenze.
/dev/sda2              13       19458   156185600    7  HPFS/NTFS

Platte /dev/sdb: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xfc32d1a9

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1       16145   129684681    7  HPFS/NTFS //edit only data here ;D
/dev/sdb2           16146       19457    26603640    5  Erweiterte
/dev/sdb5           16146       19314    25454961   83  Linux
/dev/sdb6           19315       19457     1148616   82  Linux Swap / Solaris
```

Here the actual path:
```
grub> find /boot/grub/stage1
 (hd1,4)
```



I've seen many tutorials for installing grub on the first hdd (sda) but im a bit scard that is overwrites the Windows loader or don't take the settings, so that im not able to select it from the boot menue.

Whats the best way to solve my prob? I think it could be helpful for the threadstarter too.

THX!:P

---

### Post by Acidwarlord on 2009-08-09
> **gabry79Italy said:**
> try to boot from cd live ubuntu 9.04
terminal
sudo grub
find /boot/grub/stage1
the output will be like this: (hdx,y)
root (hdx,y)
setup (hd0)
quit
If the instructions above do not work, please post :
sudo fdisk -l

If i try this, to set grub as the bootloader on my sda, will it take the settings as they are on my sdb actually?

sda win7(vista) bootloader and win partitions
sdb grub bootloader with option to boot win and ubunt. partitions

But i can only boot sda, so i need grub on sda (bevore win loader)

---

### Post by merlinus on 2009-08-09
If you set up grub to (hd0), then you can add windows to /boot/grub/menu.lst.

Given your setup, this should work:

```
sudo grub 
root (hd1,4)
setup (hd0)
quit
```

and restart.

---

### Post by Acidwarlord on 2009-08-09
> **merlinus said:**
> If you set up grub to (hd0), then you can add windows to /boot/grub/menu.lst.

Given your setup, this should work:

```
sudo grub 
root (hd1,4)
setup (hd0)
quit
```

and restart.
Thx!

without probs, i dont had to add the Wind entry to the menu.lst!! THX!

---

### Post by merlinus on 2009-08-09
Excellent!  Have fun...

---

### Post by Timmeh02 on 2009-08-10
> **raymondhenson said:**
> If this is a non-wubi install, and from the instructions of gabry (above), enter one at a time the codes ....

find /boot/grub/stage1  *(which will produce a (hdX,Y) output*
root (hdX,Y)                   *(following the output from find)*
setup (hd0)
quit
t.

If no joy, access terminal again, type and post back output of

```
fdisk -l
```

Hi, my install was from wubi.  I only get error when I follow the instructions mentioned in this thread, unless I am doing something incorrectly.  Here are the results of inputting sudo fdisk -l, regards, 
Tim

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14409   115740261    7  HPFS/NTFS
/dev/sda2           14410       14593     1477980    5  Extended
/dev/sda5           14410       14593     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```

---

### Post by gabry79Italy on 2009-08-10
> **Timmeh02 said:**
> Hi, my install was from wubi.  I only get error when I follow the instructions mentioned in this thread, unless I am doing something incorrectly.  Here are the results of inputting sudo fdisk -l, regards, 
Tim

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14409   115740261    7  HPFS/NTFS
/dev/sda2           14410       14593     1477980    5  Extended
/dev/sda5           14410       14593     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```

If your install was from wubi try to boot from windows go to 'start' and type CMD right click on this (only for vista, xp doesn't need) and 'run as administrator' after you will be in prompt  MSDOS , type and run this command:
chkdsk /r
reboot your pc AGAIN  IN WINDOWS .
After windows reboot at all, reboot again and try ubuntu

---

### Post by Timmeh02 on 2009-08-11
Unfortunately running CMD and entering chkdsk /r has not enabled me to boot into ubuntu on re-start.  I noticed when the boot screen displays it says Invalid boot.ini file or something similar, then says it's booting into windows. There is still no visible selection for ubuntu on the bootup screen.  Thanks for you help so far. Tim

---

### Post by Timmeh02 on 2009-08-15
Is there anyone out there that can help me with this problem.  I have downloaded the new wubi release today and when that re-boots there is still no option at start-up to select ubuntu. Help please.

---

### Post by ozkhalsa on 2009-08-19
HI gentlemen ,
 
I have  similar problem and hope i cna use this same thread and get some help form experts. I did a WUBI install convert by LVPM but Partition not Booting , boot GRUB was installed on Linux partition in LVPM menu and not in MBR and probably this was my mistake.

I had a perfect cofigured and working Ubuntu install on Win7 WUBI set up. I used LVPM to transfer to proper Partition. But My GRUB is is lost and only boots windows , The WUBI and New Hard install could not recue despite using Super GRUB disk.
 Error 17 or something was posted by super GRUB disc. Can boot windows on chain load but the UBuntu Install do not continue and show error.
Need script on Terminal to sort this which I am not Good at so Pls help.

Have live CD to Install.

M6400 Dell Precision 2 hardisks.

My device Map is

fd0) /dev/fd0 OEM dell
(hd0) /dev/sda Windows Vista and LInux
(hd1) /dev/sdb Windows 7

And Fdisk are here.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40ab005d

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 13 44688 358848512 7 HPFS/NTFS
/dev/sda3 44688 46339 13260800 82 Linux swap / Solaris
/dev/sda4 46342 60801 116149950 83 Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

Device Boot Start End Blocks Id System
/dev/sdb1 1 14 112423+ de Dell Utility
/dev/sdb2 * 15 19457 156175897+ 7 HPFS/NTFS
ubuntu@ubuntu:~$ 


pls help

ozkhalsa

---

