---
title: "Trouble Booting due to Adding HDD"
date: 2008-11-29
forum: Hardware
---

### Post by krionic on 2008-11-29
Yesterday I bought an external Hard Drive (1TB). Thought it was cool that it had a eSATA port, and hey, my board has one too! Plugged it in, powered up, and I get:

```
Grub 1.5

Error 17
```

I need help ultimately trying to get the drive to:
[LIST=1]
[*]Get the drive to mount in Ubuntu
[*]Proper way to update Grub so I can boot properly
[/LIST]

Here's what I've done:
Starts up fine without the drive, so I turned it off, did a little research. Figured out that my drive setup was causing a change, but couldn't figure out how to tell Grub about this change.

At this point, I can log in using the Grub SuperDisk with the external drive hooked up. At first, I couldn't get a list of installed hardware. The following is really weird.

[LIST]
[*]sudo lshw -C disk: No results. Just dropped me back at the prompt.:confused:
[*]I could still mount my drives (via Places). (Good thing Ubuntu set up fstab to start up the root drive by UUID.)
[*]SysInfo showed the external drive as attached to SCSI0 (my other 3 drives on SCSI 3, 4, & 5).
[/LIST]

I did a little more probing, and got this:

Without the external drive plugged in:
```
sudo lshw -C disk -sanitize
  *-disk:0                
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: SD15
       serial: [REMOVED]
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7b813a1f
  *-disk:1
       description: ATA Disk
       product: WDC WD5000AAKS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 12.0
       serial: [REMOVED]
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=874adc45
  *-disk
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: 02.0
       serial: [REMOVED]
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=028b0f28
  *-cdrom
       description: DVD-RAM writer
       product: SPD6104P
       vendor: PHILIPS
       physical id: 1
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NP03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```

Again, with it plugged in, I got nothing. So I tried mounting via the old mount command, and when I tried to mount sda1 I got a message saying it was not found.

I checked my BIOS and found the following setup:
SATA 1 ST3500320AS (sda)
SATA 2 WDC WD5000AAKS (sdb)
SATA 3 WDC WD2500KS (sdc)
RAID-0 WD My Book (new external drive)

It's improtant to note that in BIOS, I also have:
SATA 4 Philips SPD6104P (DVD Burner)

On a guess, I edited /boot/grub/device.map to show hd0, 1, & 2 as sdb, sdc, sdd. After that, i ran sudo update-grub.

Still getting the same error, but *some* progress. Here's the result of lshw -C disk now:

```
  *-disk                  
       description: ATA Disk
       product: WD My Book
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: [REMOVED]
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=44fdfe06

(fdisk /dev/sda1):
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    c  W95 FAT32 (LBA)

  *-disk:0
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: SD15
       serial: [REMOVED]
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7b813a1f
  *-disk:1
       description: ATA Disk
       product: WDC WD5000AAKS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 12.0
       serial: [REMOVED]
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=874adc45
  *-disk
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdd
       version: 02.0
       serial: [REMOVED]
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=028b0f28
  *-cdrom
       description: DVD-RAM writer
       product: SPD6104P
       vendor: PHILIPS
       physical id: 1
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: NP03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
```

It saw it and listed it as sda! :)
Tried to mount it, the drive showed activity on its light, then powered off. Has to be completely unplugged with the computer off to get BIOS to recognize it again.:(

Hope someone can give some hints. I've been pulling my hair out for a day now.

---

### Post by finito on 2008-11-29
Did you try using the drive on another (windows maybe) computer. Just to see if the drive works. I know its a long shot, but it is the little things for which you wanna bang your head on the wall.

---

### Post by krionic on 2008-11-29
> **finito said:**
> Did you try using the drive on another (windows maybe) computer. Just to see if the drive works. I know its a long shot, but it is the little things for which you wanna bang your head on the wall.

You are quite right. So I used the Super Grub Disk to load up my XP install, and checked the drive. It currently has about 30GB of data that I transferred to it (pictures, videos, music). I can vouch that the drive works as designed on this system using eSATA. Of course, that's in WinXP instead of Ubuntu.](*,)

---

### Post by finito on 2008-11-29
after doing some light reading it seems you have to amnually add the drive in fstab:

[http://ubuntuforums.org/archive/index.php/t-373095.html](http://ubuntuforums.org/archive/index.php/t-373095.html)

---

### Post by caljohnsmith on 2008-11-29
How about posting the output of:
```
sudo fdisk -lu
```
Also, if you want to get Ubuntu booting properly again, can you set your BIOS to boot the Ubuntu drive on start up? If so, you can install Grub to its MBR (Master Boot Record) and make it bootable by doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> makeactive
grub> setup (hdX)
grub> quit
```
Then it won't matter if you add/subtract other drives, as long as you set your BIOS to boot the Ubuntu drive. After trying the above steps, let me know how it goes or if you run into problems. :)

---

### Post by gpsmikey on 2008-11-29
There are some issues with what order the drives are found when the machine boots and you can end up with different device names depending on phase of the moon etc -- you can solve the problem by refering to the drive by it's UUID or Label (if you have the partitions labeled).  Here are some links that explain the issue a bit more and how to deal with it:

[http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)
[http://onlyubuntu.blogspot.com/2008/10/some-tips-for-correcting-uuids-in.html](http://onlyubuntu.blogspot.com/2008/10/some-tips-for-correcting-uuids-in.html)
[http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/](http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

mikey

---

### Post by krionic on 2008-11-29
**caljohnsmith,**
Results from sudo fdisk -lu:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b813a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x874adc45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   963177074   481588506   83  Linux
/dev/sdc2       963177075   976768064     6795495    5  Extended
/dev/sdc5       963177138   976768064     6795463+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x028b0f28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   488392064   244196001    7  HPFS/NTFS

```

old setup:
sda = WinXP Drive
sdb = Linux Drive
sdc = Video Editing Drive

new setup:
sda = new external drive
sdb-sdd = sda-sdc (each bumped down by one).

I'm going to try your recommended for getting grub to work again.

**finito:** No go on your recommendation. added to fstab the following line:
/dev/sda1	/media/1TB_Drive	vfat	rw,users,auto,exec,sync	0	0
Resulted in a longer boot time, but drive still not accessible. It shows it as loaded, but 0 bytes used, 0 bytes free in the File Browser.

---

### Post by krionic on 2008-11-29
**caljohnsmith,**

Thanks for the info. I'm now booting off of the loader. There's just one problem with what info you gave me. From linux, i get (hd2,0), and I followed your directions completely. When I rebooted, it failed to find the path.

I repeated the process (pressing 'c' for the command line form the boot loader), and it was listed as (hd0,0). I edited the commands (esc to return to the menu list, 'e' to edit before executing) to change the command loaded from menu.lst from (hd1,0) to (hd0,0).

That got me into Ubuntu without using the Super Grub CD. I then edited the file /boot/grub/menu.lst to show this change.:)

On the down side, now my XP isn't working (looks like I'll have to build a custom cd to do a fixboot on that drive if I can't figure out which hd command works for it)...:-k

So, all that's left is to figure out how I can get the drive working...

---

### Post by caljohnsmith on 2008-11-29
From your previous post, fdisk found your 1 TB drive just fine. How about trying to mount it with:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt &
```
Does the file browser that comes up show your files in the sda1 partition?

---

### Post by krionic on 2008-11-29
> **caljohnsmith said:**
> From your previous post, fdisk found your 1 TB drive just fine. How about trying to mount it with:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt &
```
Does the file browser that comes up show your files in the sda1 partition?

As a matter of fact, it does not...

case 1: if the drive is loaded at boot via fstab, the drive is listed as 0 bytes used, 0 bytes available (although it has about 30gigs in it). unmounting and remounting renders an error stating sda1 could not be found.

case 2: if the drive is mounted manually (no line in fstab to mount it), you get no error message and the same symptoms as in case 1.

In both case 1 & 2, upon getting a message saying sda1 cannot be found, the drive is found to have physically powered down (led light is off). Once this happens, the command 'sudo lshw -C disk' shows no disks are found (yet other internal drives are still mountable). A full lshw command shows everything except for the hard drives (working and non-working drives). Also, drive will not boot up and needs to be physically unplugged and plugged back in before the BIOS will detect it again.

---

