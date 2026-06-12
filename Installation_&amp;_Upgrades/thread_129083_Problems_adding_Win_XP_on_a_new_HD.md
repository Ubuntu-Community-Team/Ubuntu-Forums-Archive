---
title: "Problems adding Win XP on a new HD"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by nicklogan on 2006-02-12
I've been attempting to get Win XP which had already been installed on a second hard drive added to the grub boot menu with no success. The Ubuntu installation is on the slave drive, Windows XP is on the master drive.
After reading a lot of posts I tried the following :

Identified the drives :
sudo fdisk -l

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         764     6136798+  83  Linux
/dev/hdc2             765       14466   110061315    5  Extended
/dev/hdc5             765         904     1124518+  82  Linux swap / Solaris
/dev/hdc6             905        3453    20474811   83  Linux
/dev/hdc7            3454        7060    28973196   83  Linux
/dev/hdc8            7061        7364     2441848+  83  Linux
/dev/hdc9            7365        8128     6136798+  83  Linux
/dev/hdc10           8129        9337     9711261   83  Linux
/dev/hdc11           9338       10667    10683193+  83  Linux
/dev/hdc12          10668       10971     2441848+  83  Linux
/dev/hdc13          10972       11735     6136798+  83  Linux
/dev/hdc14          11736       13103    10988428+  83  Linux
/dev/hdc15          13104       14466    10948266   83  Linux

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/hdd2            3649       14592    87907680    f  W95 Ext'd (LBA)
/dev/hdd5            3649        7296    29302528+   e  W95 FAT16 (LBA)
/dev/hdd6            7297       10944    29302528+   e  W95 FAT16 (LBA)
/dev/hdd7           10945       14592    29302528+   e  W95 FAT16 (LBA)

So Ubuntu is /dev/hdc1 and Windows is /dev/hdd1.

Then following phbc50 's post in HOWTO: Restore GRUB (if your MBR is messed up) 
I did the following changing his values for my hdc1 drive:

- boot the ubuntu LIVE CD
- go in console, and change user to root with su root
- make a temp dir to mount the ubuntu partition :
mkdir /mnt/hdc1
- mount the drive with :
mount -t ext2 /dev/hdc1 /mnt/hdc1
- chroot to the mounted system :
chroot /mnt/hdc1
- run grub at the promtp : grub
then :
grub> root (<tab>
where <tab> is an actual TAB which returns the hd that grub recognises, in my case hd0 hd1
then :
grub> root (hd0,0) # in my case the hdc1 partition is recognized by grub as (hd0,0)
grub> setup (hd0)
grub> exit

I used "setup (hd0)" instead of "setup (hd0,0) because I wanted to install to the drive and not to the partition.

After rebooting Windows was still not listed in the grub boot menu so I tried editing  /boot/grub/menu.lst~ and added the following :

# This entry added on 02/12/06 to add Windows XP Professional booting from
# hdd1 (or hd1,0 as identified from the "grub> root (<tab>" listing)
title Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST


Still no Windows option in grub after saving and rebooting! Am I trying to set this up on the wrong drive? Does cable position matter? Do I have to map the drive in grub? What? Please help. Ubuntu boots fine but windows is invisible and I need to use a CAD program occasionally. Any suggestions or error determination would be appreciated.

---

### Post by Sutekh on 2006-02-12
i'm not sure why the HOWTO didn't work, but

[QUOTE=nicklogan]
After rebooting Windows was still not listed in the grub boot menu so I tried editing  /boot/grub/menu.lst~ and added the following :
[/QUOTE]
You should have edited /boot/grub/menu.lst **not** /boot/grub/menu.lst~

[QUOTE=nicklogan]
then :
grub> root (<tab>
where <tab> is an actual TAB which returns the hd that grub recognises, in my case hd0 hd1
then :
grub> root (hd0,0) # in my case the hdc1 partition is recognized by grub as (hd0,0)
grub> setup (hd0)
grub> exit[/QUOTE]
Just to be 100%, check the file /boot/grub/device.map.  It should look like this
```

(hd0)   /dev/hdc
(hd1)   /dev/hdd

```
It would make me feel sure that (hd1,0) is the proper location to boot Windows from.

---

### Post by lha on 2006-02-13
Whoa, you do have a lot of partitions. :)

As Sutekh already pointed, you have edited wrong file. There shouldn't be a '~' in the end. I noticed also another thing you need to change. After
'title Windows XP' you should have
'map (hd0) (hd1)'
'map (hd1) (hd0)'.

So the thing you have add to menu.lst is

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1

---

### Post by nicklogan on 2006-02-13
Thanks to both of you for your help. After checking the device.map file as Sutekh suggested, i found that only hdc was listed. Adding lha's script to the CORRECT file (menu.lst) caused Windows to appear in the menu and boot properly.
BTW, I have a lot of partitions because I was trying out a variety of Linux distributions - Ubuntu won out as my main distribution with Ubuntu64 to play with also and Mandrake (my main distribution for years) was given the boot.

---

### Post by leks29 on 2007-06-06
i have a very similar problem, i had to reinstall my windows xp, and so i formated its partition, afterwards i was able to recover and get into ubuntu, but i cant manage t boot windows any help is apreciated, what do i do to give u more info, im pretty new to linux so if u help me by telling me what command can give u something to help me ill be glad...

this what i have done until now:

my hard drive is partitioned into 3, partition one used to have windows, partition 2 has ubuntu, and partition 3 was free space for documents (i dont like to store my personal files in the same partition where the Os is), so after my windows crashed i formated the partition and moved the files in the third partition to the first one(why because is smaller and i wanted a place to backup), but then 2 weeks later i reinstalled my windows but this time in the third partition, yeah i had to recover my grub from the live cd but when i added the windows partiton to the grub it says        

this is my partition list:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        3200    25703968+   7  HPFS/NTFS
/dev/sda2            3201        6400    25704000   83  Linux
/dev/sda3            6401        9600    25704000    f  W95 Ext'd (LBA)
/dev/sda4   *        9601        9729     1036192+  82  Linux swap / Solaris
/dev/sda5            6401        9600    25703968+   7  HPFS/NTFS
       

this is my grub menu list:

title		Windows XP
root 		(hd0,2)
savedefault
makeactive
chainloader 	+1

title		Ubuntu, kernel 2.6.20-16-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro single
initrd		/boot/initrd.img-2.6.20-16-lowlatency

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro single
initrd		/boot/initrd.img-2.6.20-15-lowlatency

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=12a73024-a4e6-46df-bd8f-6d527abccd64 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

what else can i do to give you more info.... please help this newby!!!!

also does my menu.lst file needs all those boot options?

---

