---
title: "External drive isn't mounting...."
date: 2009-12-11
forum: Hardware
---

### Post by basicxman on 2009-12-11
Hi there, I have an external 500GB Seagate USB drive.  It is currently working flawlessly in Windows, and was working with ubuntu about a week ago.  Ubuntu doesn't seem to be mounting it properly now.  Not exactly sure what's going on with it.  Here's some data for you, thanks for any help!

$ sudo mount -a 
<no effect>

$ lsusb
Bus 002 Device 005: ID 0bc2:3300 Seagate RSS LLC 
Bus 002 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

<upon plugging in the device>
$ dmesg | tail
[  685.549180] scsi 7:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
[  685.549985] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  685.550628] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  685.552134] sd 7:0:0:0: [sdb] Write Protect is off
[  685.552141] sd 7:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[  685.552146] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  685.554935] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  685.554945]  sdb: sdb1
[  685.584186] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  685.584195] sd 7:0:0:0: [sdb] Attached SCSI disk

<upon unplugging the device>
$ dmesg | tail
[  685.549985] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  685.550628] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  685.552134] sd 7:0:0:0: [sdb] Write Protect is off
[  685.552141] sd 7:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[  685.552146] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  685.554935] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  685.554945]  sdb: sdb1
[  685.584186] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  685.584195] sd 7:0:0:0: [sdb] Attached SCSI disk
[  709.770934] usb 2-3: USB disconnect, address 6

Formatted as NTFS.

Ubuntu seems to be realising that I've plugged a drive in, just not working??

$ cd /dev
$ ls
$ adsp             loop5               ram8        tty13  tty42    usbmon0
agpgart          loop6               ram9        tty14  tty43    usbmon1
audio            loop7               random      tty15  tty44    usbmon2
binder           mapper              rfkill      tty16  tty45    usbmon3
block            mcelog              rtc         tty17  tty46    usbmon4
bus              mem                 rtc0        tty18  tty47    usbmon5
cdrom            mixer               scd0        tty19  tty48    usbmon6
cdrw             net                 sda         tty2   tty49    usbmon7
char             network_latency     sda1        tty20  tty5     v4l
console          network_throughput  sda2        tty21  tty50    vboxdrv
core             null                sda5        tty22  tty51    vboxnetctl
cpu_dma_latency  oldmem              sdb         tty23  tty52    vcs
disk             pktcdvd             sdb1        tty24  tty53    vcs1
dri              port                sequencer   tty25  tty54    vcs2
dsp              ppp                 sequencer2  tty26  tty55    vcs3
dvd              psaux               sg0         tty27  tty56    vcs4
dvdrw            ptmx                sg1         tty28  tty57    vcs5
ecryptfs         pts                 sg2         tty29  tty58    vcs6
fb0              ram0                shm         tty3   tty59    vcs7
fd               ram1                snapshot    tty30  tty6     vcs8
full             ram10               snd         tty31  tty60    vcsa
fuse             ram11               sndstat     tty32  tty61    vcsa1
hidraw0          ram12               sr0         tty33  tty62    vcsa2
hpet             ram13               stderr      tty34  tty63    vcsa3
input            ram14               stdin       tty35  tty7     vcsa4
kmsg             ram15               stdout      tty36  tty8     vcsa5
log              ram2                tty         tty37  tty9     vcsa6
loop0            ram3                tty0        tty38  ttyS0    vcsa7
loop1            ram4                tty1        tty39  ttyS1    vcsa8
loop2            ram5                tty10       tty4   ttyS2    video0
loop3            ram6                tty11       tty40  ttyS3    zero
loop4            ram7                tty12       tty41  urandom

$ cd ./sdb1
$ bash: cd: ./sdb1: Not a directory

---

### Post by ibuclaw on 2009-12-11
Try the debugging steps in: [https://wiki.ubuntu.com/DebuggingRemovableDevices#How%20to%20report](https://wiki.ubuntu.com/DebuggingRemovableDevices#How%20to%20report)

Does this issue follow to another user on the workstation? You can test by creating a new account and try logging in.

Regards
Iain

---

### Post by basicxman on 2009-12-11
It doesn't work on another user, I've went into System->Admin->Disk Utility and it's listed under there, after trying Edit->Mount I get the following error:

Error mounting: mount exited with exit code 21: The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
can't create lock file /etc/mtab~4495: Invalid argument (use -n flag to override)

---

### Post by basicxman on 2009-12-11
Oh BTW, using Ubuntu 9.10 with all the latest updates and latest kernel.

---

### Post by ibuclaw on 2009-12-12
> **basicxman said:**
> It doesn't work on another user, I've went into System->Admin->Disk Utility and it's listed under there, after trying Edit->Mount I get the following error:

Error mounting: mount exited with exit code 21: The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
can't create lock file /etc/mtab~4495: Invalid argument (use -n flag to override)

[LIST=1]
[*]Mount and Unmount/Eject the device cleanly in Windows.
If still failing:
[*]Run a chkdsk on the filesystem from Windows and retry. (In the mount properties under the Tools tab).
If still failing:
[*]Run a fsck on the filesystem from Linux and retry. (Run gparted, and select check filesystem).
If still failing:
[*]Use the force clean tool from ntfsprogs on Linux.
```
sudo ntfsfix /dev/sdb1
```
[/LIST]
Although, the first two steps - if not the first alone - should fix your issue.

Regards
Iain

---

