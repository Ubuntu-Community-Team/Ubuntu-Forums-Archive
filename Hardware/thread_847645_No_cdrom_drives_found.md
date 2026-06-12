---
title: "No cdrom drives found"
date: 2008-07-02
forum: Hardware
---

### Post by plugugly on 2008-07-02
I posted this over in absolute beginner talk, and think it probably belongs here:

Hello, I need some help. I have a Gateway 7330GZ laptop that I was doing a cleaning session on, I decided while I was playing around I would format and try Ubuntu, so I burned the boot disc and installed it as my only operating system.

I've been struggling ever since. I have had issues with it correctly working with anything on this laptop. I decided I would do dual boot and try to figure the sound and other stuff out while I had XP up and running again.

I discovered that it is not finding my cd-rom at all since the install. It lights up and spins up like normal, but no icon appears, if I try to use Audio sound Extractor, it gives me "No cd-rom drives found".

I searched here, but everyone wants the output of terminal command to help, and none looked like mine.

I'm a complete newb and would really like some help. Here's my terminal thing other people asked for in other threads:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=b1340fad-3b1f-4f65-bb17-224946f16208 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=6b896adf-4afd-443f-bbd0-7302b4b0b99f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by plugugly on 2008-07-03
Really? No help available for this? I can't do anything with my laptop until I solve this problem.

Please help. Any suggestions on getting the cdrom to work would be appreciated.

---

### Post by tipiglen on 2008-07-04
The problem is probably in your fstab file ( the table of filesystems  mounted on booting up)

You'll need to go to a terminal (upper left, Applications/accessories/terminal)

Then enter 
```
sudo cat /etc/fstab
```
enter your password, and you'll get something a little like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f62e3f18-02e0-486f-b46a-54a67f105f08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d3dd670e-5b93-4d68-a2de-445b5a31e3ec none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# hopefully this will get share partition mounted at boot
/dev/sda2 /media/disk-6 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
# same for windows partition mounted at boot
#/dev/sda1 /media/25_02_42_ fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
ed@ubuntu:~$ 
```
lines beginning with # are 'comments' and do nothing. 
The line you'll be interested in will be the one like the one above beginning /dev/cdrom....but I'll bet yours says /dev/scd0 or the like

If so, try ```

sudo lshw -C disk

```
and you should get a list containing a section like this
```
*-cdrom:0
description: DVD writer
product: DVD RW DW-D22A
vendor: SONY
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/cdrom1
logical name: /dev/dvd1
logical name: /dev/scd0
logical name: /dev/sr0
logical name: /media/cdrom0
version: BFS1
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready 
```
Take note of the FIRST logical name (write it down), and do
```
sudo gedit /etc/fstab
```
This will open the fstab file for editing.
Carefully move your cursor to the line beginning /dev/scd0 and change /dev/scd0 to the logical name you wrote down (probably /dev/cdrom)
Save the file and exit gedit (file/quit)

reboot and your cdrom should be working again.

Good luck
Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by mahiyar on 2009-01-05
Just an addition, because having the same problem this is the first page I found. for me the solution of tipiglen did not work, what did work was to completely comment out / delete the cdrom lines from 'fstab'

---

### Post by Macr237 on 2009-01-19
I think I am having a similar issue. I have 2 drives, cdrom:1 is a Liteon DVD multi recorder with light scribe and cdrom:0 is a CD-R/CD-RW writer. My issue is I can't get the DVD to play any DVD's through mediaplayer or VLC (preferred player). The DVD appears to be mounted and comes up on the desktop with the icon and the name of the DVD, but that is about it.

When I enter ```
sudo cat /etc/fstab
``` I get ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=75dda32c-2b95-4739-8191-da1d700f1596 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5c1ebbb7-9248-4aa8-a690-2ccea578fb24 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

When I enter ```
sudo lshw -C disk
``` I get ```
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SP2514N
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: VF10
       serial: S08BJ1DP113828
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b309b309
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=ready
  *-cdrom:1
       description: DVD-RAM writer
       product: DVDRW SHM-165H6S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom0
       version: HS0E
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

```
I have the DVD on the end of the ribbon cable as well. Any ideas?

TIA

---

### Post by hanniph on 2009-01-20
ok, have some similar problems. cdrom refuses to work anymore. Furthermore 
sudo lshw -C disk doesn't output any cdrom disk. (only hard drive).

In /etc/fstab I have this line:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
and in my /dev directory there is no scd0. I am really confused about this :?:
Any help appreciated

---

### Post by Captaingracekidd on 2009-02-02
Hi, Im experiencing the same problems as hanniph. 
That is no cd rom listed at all.  

The cdrom worked with my previous Gutsy installation but not in my newly installed Intrepid. I installed it from a fresh live cd and all.

Please help.

---

### Post by hanniph on 2009-02-13
huh, that's annoying isn't it? :) Anyway, I figured that my CD-ROM is "dead" since even BIOS cannot detect it. And if BIOS doesn't detect it no OS will. So be sure to check whether your CD drive is detected by BIOS

---

### Post by Captaingracekidd on 2009-02-18
Oki, but how can it be dead if it recognizes discs and spins them?
I will check the bios to be sure but I know the disc has been working perfectly before with the same noises and such as now.

---

