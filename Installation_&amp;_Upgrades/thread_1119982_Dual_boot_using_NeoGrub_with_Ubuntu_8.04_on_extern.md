---
title: "Dual boot using NeoGrub with Ubuntu 8.04 on external drive doesn't work (error 19)"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Nilfisken on 2009-04-08
I surrender myself! After two days of trying to make this work and reading over 10 different tutorials I've decided to seek help!

So here's my problem:

I've previously had a Vista/Ubuntu dual-boot configuration on my laptop, but it didn't always work as fantastic, as I would have liked, so I had to let Ubuntu go, since I need to use Vista most of the time :( 

However, I didn't want to be entirely without Ubuntu, so I decided to try and install it on to my external hdd (USB). And this is how I did it:


Using the Ubuntu 8.04 live-cd I installed Ubuntu onto the external hdd, BUT since I didn't want GRUB to inflict on my Vista MBR, I set GRUB to install itself on the ext drive (hd1 in my case).

So that's all good. I wanted EasyBCD to be in charge of booting, so I added a Linux entry and pointed it to my root Ubuntu partition on the ext hdd - and restarted... I chose the Ubuntu option in the boot loader menu - but that only led me to the Grub Commandline (if I remember it right)...


I read some more tutorials, and tried to choose "GRUB isn't installed to the bootsector" in EasyBCD, thereby adding the NeoGrub loader. I used the Ubuntu LiveCD to extract the original GRUB menu.lst boot information, and pasted it into the NeoGrub menu.lst file. I tried rebooting and...

... I got to the NeoGrub bootloader (Grub4Dos?) screen, clicked on the first of the three Ubuntu options and *sigh* got an "Error 19: Cannot mount selected partition"

I've tried all sorts of fiddling, to make it work since, but this is sort of where it always ends. 
So if anyone has any suggestions on what to do, I'd be thankful :) I really want this to work - I miss Ubuntu.


The external drive is a 1tb WD MyBook Essential USB (not sure if it matters).

I ran the boot info script using the LiveCD and got the following information:

> ============================= Boot Info Summary: ============================== 

 => Windows is installed in the MBR of /dev/sda 
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst. 

sda1: _________________________________________________________________________ 

    File system:       vfat 
    Boot sector type:  Vista: Fat 32 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD 

sda2: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows Vista 
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe 

sda3: _________________________________________________________________________ 

    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:  

sda5: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista 
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048. 
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________ 

    File system:       vfat 
    Boot sector type:  MSWIN4.1: Fat 32 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________ 

    File system:       vfat 
    Boot sector type:  Fat32 
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1754008830. 
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________ 

    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:  

sdb5: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2 
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab 

sdb6: _________________________________________________________________________ 

    File system:       swap 
    Boot sector type:  - 
    Boot sector info:  

=========================== Drive/Partition Info: ============================= 

Drive: sda ___________________ _____________________________________________________ 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
129 heads, 4 sectors/track, 605778 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xf1b06308 

Partition  Boot         Start           End          Size  Id System 

/dev/sda1               2,048    14,338,047    14,336,000  1c Hidden W95 FAT32 (LBA) 
/dev/sda2    *     14,338,048   193,284,095   178,946,048   7 HPFS/NTFS 
/dev/sda3         193,284,096   312,578,047   119,293,952   f W95 Ext d (LBA) 
/dev/sda5         193,286,144   312,578,047   119,291,904   7 HPFS/NTFS 


Drive: sdb ___________________ _____________________________________________________ 

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xe8900690 

Partition  Boot         Start           End          Size  Id System 

/dev/sdb1    *             63 1,679,402,969 1,679,402,907   c W95 FAT32 (LBA) 
/dev/sdb2       1,754,008,830 1,953,520,064   199,511,235   b W95 FAT32 
/dev/sdb3       1,679,402,970 1,754,008,829    74,605,860   5 Extended 
/dev/sdb5       1,679,403,033 1,750,860,089    71,457,057  83 Linux 
/dev/sdb6       1,750,860,153 1,754,008,829     3,148,677  82 Linux swap / Solaris 


blkid -c /dev/null: ____________________________________________________________ 

/dev/sda1: LABEL="RECOVERY" UUID="80E9-C15B" TYPE="vfat" 
/dev/sda2: UUID="94029B60029B4660" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="06189E1F189E0E35" LABEL="DATA" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="My Book" UUID="0DC8-8AE0" TYPE="vfat" 
/dev/sdb2: LABEL="DiskII" UUID="49DB-EABE" TYPE="vfat" 
/dev/sdb5: UUID="6e969ec0-180c-41ee-b9a2-4eed8613af86" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="b7a2a05e-8405-405e-b775-182433442a66" 

=============================== "mount" output: =============================== 

proc on /proc type proc (rw) 
sysfs on /sys type sysfs (rw) 
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755) 
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
udev on /dev type tmpfs (rw,mode=0755) 
devshm on /dev/shm type tmpfs (rw) 
devpts on /dev/pts type devpts (rw,gid=5,mode=620) 
tmpfs on /tmp type tmpfs (rw,nosuid,nodev) 
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu) 
/dev/sdb2 on /media/DiskII type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush) 
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush) 
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal) 


The original GRUB menu.lst file on the Ubuntu partition looks like this:
> ## ## End Default Options ## 

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic 
root		(hd1,4) 
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic 
quiet 

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) 
root		(hd1,4) 
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic 

title		Ubuntu 8.04.2, memtest86+ 
root		(hd1,4) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 


The NeoGrub menu.lst looks like this (I've made a lot of entries, to keep track of what I've changed - none of them work however. Second and third are the same):
> # Second

title NOWORK II Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd1,4)


kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro quiet splash

initrd /boot/initrd.img-2.6.24-23-generic
quiet

title NOWORK II Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd1,4)


kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro single
initrd /boot/initrd.img-2.6.24-23-generic



title NOWORK II Ubuntu 8.04.2, memtest86+

root (hd1,4)

kernel /boot/memtest86+.bin

quiet

# Third

title Ubuntu 8.04.2, kernel 2.6.24-23-generic 
root (hd1,4) 
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro quiet splash 
initrd /boot/initrd.img-2.6.24-23-generic 
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) 
root (hd1,4) 
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro single 
initrd /boot/initrd.img-2.6.24-23-generic 

title Ubuntu 8.04.2, memtest86+ 
root (hd1,4) 
kernel /boot/memtest86+.bin 
quiet

# Fourth Changed (hd1,4) to (hd0,4) - gave an error 17: file not found.

title Ubuntu 8.04.2, kernel 2.6.24-23-generic 
root (hd0,4) 
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro quiet splash 
initrd /boot/initrd.img-2.6.24-23-generic 
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) 
root (hd0,4) 
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro single 
initrd /boot/initrd.img-2.6.24-23-generic 

title Ubuntu 8.04.2, memtest86+ 
root (hd0,4) 
kernel /boot/memtest86+.bin 
quiet


I am more or less a Ubuntu and GRUB novice, so you may have to be a bit patient with me :)

Thanks in advance

---

### Post by meierfra. on 2009-04-10
A few things to try:


1)   Add 

title Ubuntu 8.04.2, kernel 2.6.24-23-generic  (hd0,4)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=6e969ec0-180c-41ee-b9a2-4eed8613af86 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

to the Ubuntu grub menu. Then set your bios to boot from the USB drive. If you get the grub menu, choose the (hd0,4) entry.


2)  Install grub to the boot sector of the Ubuntu partition:

```
sudo grub
```
and at the grub prompt:

```
root (hd1,4)
setup (hd1,4)
quit
```

Then try  this again:

> so I added a Linux entry and pointed it to my root Ubuntu partition on the ext hdd 


3)  At the NeoGrubScreen, press "c" and type

```
geometry (hd0)
geometry (hd1)
```

This should list the partitions on your hard drive and on the USB drive.
Let me know if the USB drive is correctly detected.

---

### Post by Nilfisken on 2009-04-15
Thanks for the suggestions meierfra - unfortunately they didn't get me any further :( - but now I may know a bit about why.

It might just be my BIOS that's acting weird. It seems that it doesn't detect my external HDD as a "portable device", but as a secondary hard drive, so in order to boot from it, I need to set my external hdd as being the primary boot harddisk, thereby overriding my internal harddrive (and it's bootsector) completely.

So with GRUB installed in the bootsector of my ext. hdd, you should think, that it would actually be able to boot, now that it's in command of booting - but no.

I actually do get to the GRUB boot stage 1.5 - but no further. It just stops there giving me an "error 17".

Any ideas on how to get further from here.

---

### Post by meierfra. on 2009-04-15
I just noticed, that I had a typo  in number 2) from my previous post. I fixed it.  (I wanted to say "setup (hd1,4)", not "setup (hd1)"). So could you try 2) again?


> It might just be my BIOS that's acting weird.
 
Very plausible.

Here are a few more things to try:

4)  Boot from the LiveCD, open a terminal and run a file system check

```
sudo umount /dev/sdb5
sudo e2fsck -fyv /dev/sdb5

```
(it's ok if the first command returns "/dev/sdb5 is not mounted")

5) Check out your bios.  Look for setting related to "LBA", "AHCI", "IDE", "RAID" . Try out various setting, but make sure to record the original settings.

6) Your boot files are beyond the 137 GB limit, which can cause grub error 18 and in some  cases also grub error 17. So if all else fails you might consider reinstalling and create a small 200 MB boot partition at the beginning of /dev/sdb.

---

### Post by Nilfisken on 2009-04-20
I think I'll just try option 6) to begin with (as I have a weak recollection of some error along the way saying that the bootsector was too big for the bios to handle - or something like that). 

But what type of partition would that first 200 Mb need to be? FAT32? ext..? Something else?

---

### Post by meierfra. on 2009-04-20
> But what type of partition would that first 200 Mb need to be? FAT32? ext..? Something else?
I would  suggest Ext2 or Fat32.
Ext2 is the better file system.
Fat32 has a little bit more flexibility, for example  a Fat32 boot partition can also be used for the Windows boot files.
So use Ext2. But if you like to experiment with different setups, you might want to use fat32 instead.

---

