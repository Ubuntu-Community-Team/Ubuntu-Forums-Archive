---
title: "Cannot see WD 320GB External USB HDD"
date: 2008-12-21
forum: Hardware
---

### Post by muxpux on 2008-12-21
Hi all just new to the linux world and am having trouble trying to connect a Western Digital 320GB USB HDD it is not showing up when i plug it in, you can hear it spinning up and clicking but nothing mounted, it's formatted in FAT32 and works fine in windows XP any help would be greatly appreciatted.
Thanks Dan

---

### Post by Nexano on 2008-12-21
If you dont need it to be readable by windows, reformat it as ext3, if you need it for windows as well, format it as NTFS. I dont know how well Ubuntu and FAT32 works together, but i know that NTFS is readable and writable.

---

### Post by muxpux on 2008-12-21
i would reformat it but it doesn't show up to give me that option

---

### Post by albinootje on 2008-12-21
> **muxpux said:**
> Hi all just new to the linux world and am having trouble trying to connect a Western Digital 320GB USB HDD it is not showing up when i plug it in, you can hear it spinning up and clicking but nothing mounted, it's formatted in FAT32 and works fine in windows XP any help would be greatly appreciatted.
Thanks Dan

Can you plug the disk in, and post the output of :
```

sudo fdisk -l
mount
cat /etc/fstab

```

---

### Post by Tsume on 2008-12-21
> **albinootje said:**
> Can you plug the disk in, and post the output of :
```

sudo fdisk -l
mount
cat /etc/fstab

```

I've got the same issue on my Acer Travelmate 2423WXCi with a 180GB generic Hitachi USB drive.

```
tsumeone@TranscensionNIX /dev $ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085e07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
tsumeone@TranscensionNIX /dev $ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tsumeone/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tsumeone)
tsumeone@TranscensionNIX /dev $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ce8901a1-7ca0-4b81-a537-1e7ce2beff5c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6e40a89c-0b23-41e6-b8da-80338ca93a09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tsumeone@TranscensionNIX /dev $ 

```

Additionally, I didn't see anything resembling a "sdb" in /dev... also, ubuntu 8.10 will not boot with this drive plugged in, the progress bar gets to 1/8 and sits there with no activity on the drive or laptop.  The second I unplug the drive, it starts loading again.

Edit:  Bug report is here, please comment / nominate on it so it gets noticed and fixed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960)

---

### Post by muxpux on 2008-12-22
Just a note i installed ubuntu on my brothers spare hdd on his computer and the external drive mounts staight away, both installations are a day apart


> **albinootje said:**
> Can you plug the disk in, and post the output of :
```

sudo fdisk -l
mount
cat /etc/fstab

```

taylor@taylors:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa500a500

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24134   193856323+  83  Linux
/dev/sda2           24135       24321     1502077+   5  Extended
/dev/sda5           24135       24321     1502046   82  Linux swap / Solaris


taylor@taylors:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7de49618-5ba4-4575-a117-9b8e72c5ff37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=65fa55a5-fb0b-4e34-904e-9158803ceddc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

thanks for the replys so far hope this helps

---

### Post by Yellow Pasque on 2008-12-22
> **muxpux said:**
> i would reformat it but it doesn't show up to give me that option
You shouldn't need to reformat it. Linux can read FAT32 partitions just fine, so I don't think that's the issue (although FAT32 can't store files larger than 4GB and is relatively slow).

fdisk isn't even showing the drive, so I'm thinking it might be a USB issue. Does an lsusb command show the drive when plugged in?

---

### Post by Tsume on 2008-12-23
> **Temüjin said:**
> You shouldn't need to reformat it. Linux can read FAT32 partitions just fine, so I don't think that's the issue (although FAT32 can't store files larger than 4GB and is relatively slow).

fdisk isn't even showing the drive, so I'm thinking it might be a USB issue. Does an lsusb command show the drive when plugged in?

lsusb entry showing drive:
```
Bus 005 Device 002: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller

```

Yeah, it recognizes that it's plugged in, the problem seems to be between when the drive is plugged in and translated into being a mass storage device (/dev/sdb is never created).  My CPU usage goes thru the roof and my dmesg logs are completely spammed full of the "Sense" error messages.  I hope they fix it, this is a serious regression... drive worked with older kernels (I know earlier 2.6.x worked, I think it was 2.6.24 last time I used it and it worked...) on the same pc.

dmesg problem snippet:
```
[25702.515484] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[25702.515489] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information

```

---

### Post by albinootje on 2008-12-23
> **Tsume said:**
> lsusb entry showing drive:
```
Bus 005 Device 002: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller

```

Yeah, it recognizes that it's plugged in, the problem seems to be between when the drive is plugged in and translated into being a mass storage device (/dev/sdb is never created).  My CPU usage goes thru the roof and my dmesg logs are completely spammed full of the "Sense" error messages.  I hope they fix it, this is a serious regression... drive worked with older kernels (I know earlier 2.6.x worked, I think it was 2.6.24 last time I used it and it worked...) on the same pc.

dmesg problem snippet:
```
[25702.515484] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[25702.515489] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information

```

Did you file a bug-report already ?
Just wondering.

---

### Post by Tsume on 2008-12-23
I found the bug already reported and linked it in post #4

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960)

Almost a month and no indication it is being looked at... more people need to comment / nominate it.

---

### Post by muxpux on 2008-12-23
> **Temüjin said:**
> You shouldn't need to reformat it. Linux can read FAT32 partitions just fine, so I don't think that's the issue (although FAT32 can't store files larger than 4GB and is relatively slow).

fdisk isn't even showing the drive, so I'm thinking it might be a USB issue. Does an lsusb command show the drive when plugged in?

Just plugged in today and it was trying to mount popping up on desktop then dissapearing came up with a error message

[IMG]http://i58.photobucket.com/albums/g242/mxpx0000/Screenshot.png[/IMG]

But at least it is sort of recognising it

taylor@taylors:~$ lsusb
Bus 005 Device 008: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:0714 Microsoft Corp. 
Bus 001 Device 004: ID 045e:0707 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by muxpux on 2008-12-23
Hi Guys, I've Solved it! i read a post in [here]("http://ubuntuforums.org/showthread.php?t=1019097") about being not enough power and remembered reading about a jumper setting on the motherboard for ps2_usb_PWR1 power, i just switched this from +5VSB to +5V and the drive mounted instantly, Thanks for all your help and i hope it helps others!

---

### Post by Tsume on 2008-12-23
Glad you were able to fix it on your end!

They will need to revert whatever kernel change broke it on my end to fix it here though, as my laptop doesn't have jumper settings.  It did work on older kernels and does work on windows xp/vista, not sure why it hates me right now.

---

### Post by Ber P on 2009-01-02
I'm having the same problem with a Maxtor 5000DV drive. Worked perfectly under Gutsy, but I also get the *Sense Key: No Sense* error under Ibex. 
Tried to chkdsk and reformat the drive in windows, but no luck. 
Guess we just have to wait until someone fixes the kernel :(

---

### Post by albinootje on 2009-01-02
> **Ber P said:**
> I'm having the same problem with a Maxtor 5000DV drive. Worked perfectly under Gutsy, but I also get the *Sense Key: No Sense* error under Ibex. 
Tried to chkdsk and reformat the drive in windows, but no luck. 
Guess we just have to wait until someone fixes the kernel :(

I know it might sound as a crazy idea, but you could use Ubuntu Gutsy in VirtualBox just for copying from/to your usb-disk in your Ubuntu Hardy or Intrepid installation.

Usb-support in VirtualBox should work well with a variety of usb-sticks and usb-disks (but not necessarily with usb-printers).

Use the "shared folders" in VirtualBox on the /media directory (that'll include usb-disks!) and you're set.

This setup will save you booting into "that other well known OS from Redmond,WA,USA".

---

### Post by Ber P on 2009-01-02
Actually I'm using it from *¤cough¤* windows *¤cough¤* in VirtualBox in the moment.  :D
I'm unfortuanatly still using applications that has no linux replacement and won't run under Wine, so it is installed anyway.

---

### Post by Tsume on 2009-01-07
I just use mine with my other pc for now.  I don't want to go through the hassle of using Virtualbox with an older version of Ubuntu, although it is definitely a way to make my drive work.  I'd like it if this bug got the attention it deserved as a kernel regression and they fixed it, since it used to work.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960)

---

