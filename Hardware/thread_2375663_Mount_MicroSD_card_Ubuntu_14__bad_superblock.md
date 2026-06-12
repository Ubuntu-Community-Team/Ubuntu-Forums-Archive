---
title: "Mount MicroSD card Ubuntu 14 / bad superblock"
date: 2017-10-26
forum: Hardware
---

### Post by waterwheel3 on 2017-10-26
I've got a microSD card reader (from canakit) that I'm trying to use.  I can't get the card reader to mount.  

When I insert the card reader into the PC, it recognizes the reader.  output from syslog:
> Oct 26 08:55:40 glenn-desktop kernel: [48907.728536] sd 9:0:0:0: [sde] 0 512-byte logical blocks: (0 B/0 B)
Oct 26 08:55:40 glenn-desktop kernel: [48907.728544] sd 9:0:0:0: [sde] 31207423-byte physical blocks
Oct 26 08:55:40 glenn-desktop kernel: [48907.729235] sd 9:0:0:0: [sde] Write Protect is off
Oct 26 08:55:40 glenn-desktop kernel: [48907.729242] sd 9:0:0:0: [sde] Mode Sense: 03 00 00 00
Oct 26 08:55:40 glenn-desktop kernel: [48907.729902] sd 9:0:0:0: [sde] No Caching mode page found
Oct 26 08:55:40 glenn-desktop kernel: [48907.729917] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct 26 08:55:40 glenn-desktop kernel: [48907.733778] sd 9:0:0:0: [sde] Unsupported sector size 31207423.
Oct 26 08:55:40 glenn-desktop kernel: [48907.735452] sd 9:0:0:0: [sde] No Caching mode page found
Oct 26 08:55:40 glenn-desktop kernel: [48907.735466] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct 26 08:55:40 glenn-desktop kernel: [48907.735475] sd 9:0:0:0: [sde] Attached SCSI disk


And from this:  ls -la /dev/sd*

> brw-rw---- 1 root disk 8, 64 Oct 26 08:55 /dev/sde
Which is the microsd card reader.  So, it's there.

However this:  mount /dev/sde /mnt produces:
> mount: /dev/sde: can't read superblock

A variety of other tools and attempts continue to boil down to pretty much that same problem.

Also tried a different SD card (both are new).  Identical results.  That leaves two sources - I've got a bad reader, or I'm an idiot.  Safe bet to start (since the machine at least recognizes the reader) is the second one.  Thoughts on what I should try next please?

---

### Post by sudodus on 2017-10-26
Did you try to mount with superuser privileges? And mount the relevant partition, not the whole drive)?

```
sudo mount /dev/sdxn /mnt
```

where x is the drive letter and n is the partition number, so for example

```
sudo mount /dev/sde1 /mnt
```

You can also have a look at this link,

[How do I use 'chmod' on an NTFS (or FAT32) partition?](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)

---

### Post by waterwheel3 on 2017-10-26
Thanks for the feedback.

Those commands don't work, because there's no partition.  /dev/sde exists and shows up, but /dev/sde1 does not exist - so those commands just error out. 

I'm not clear if the lack of existence of sde1 partition is because the SD cards are new and unformatted, or because it's symptomatic of the problems I'm having otherwise.

---

### Post by sudodus on 2017-10-26
When the Micro SD cards are connected, please post the output of the following commands

```
df
sudo parted -ls
sudo lsblk -f
sudo lsblk -m
```

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by waterwheel3 on 2017-10-26
df - no sign of the card reader
```
Filesystem      1K-blocks      Used  Available Use% Mounted on
udev              3784896         8    3784888   1% /dev
tmpfs              765860      1280     764580   1% /run
/dev/sda1       453622248 355689516   74866928  83% /
none                    4         0          4   0% /sys/fs/cgroup
none                 5120         0       5120   0% /run/lock
none              3829284       420    3828864   1% /run/shm
none               102400        52     102348   1% /run/user
/dev/sdc1      1922728752 854534800  970501896  47% /weekly-archives
/dev/sdd1      1922728752     68956 1824967740   1% /monthly-archives
/dev/sdb1      1922728752 166878728 1658157968  10% /backup

```

parted -ls (no sign again)
```
Model: ATA Crucial_CT480M50 (scsi)
Disk /dev/sda: 480GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  472GB  472GB   primary   ext4            boot
 2      472GB   480GB  8049MB  extended
 5      472GB   480GB  8049MB  logical   linux-swap(v1)


Model: ATA WDC WD20EZRZ-60Z (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA WDC WD2003FYYS-0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA WDC WD20EZRZ-60Z (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4
```

lsblk -f (no sign)
```
NAME   FSTYPE LABEL            MOUNTPOINT
sda                            
&#9500;&#9472;sda1 ext4                    /
&#9500;&#9472;sda2                         
&#9492;&#9472;sda5 swap                    [SWAP]
sdb                            
&#9492;&#9472;sdb1 ext4   backup           /backup
sdc                            
&#9492;&#9472;sdc1 ext4   weekly-archives  /weekly-archives
sdd                            
&#9492;&#9472;sdd1 ext4   monthly-archives /monthly-archives

```

lsblk -m
```
NAME     SIZE OWNER GROUP MODE
sda    447.1G root  disk  brw-rw----
&#9500;&#9472;sda1 439.6G root  disk  brw-rw----
&#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5   7.5G root  disk  brw-rw----
sdb      1.8T root  disk  brw-rw----
&#9492;&#9472;sdb1   1.8T root  disk  brw-rw----
sdc      1.8T root  disk  brw-rw----
&#9492;&#9472;sdc1   1.8T root  disk  brw-rw----
sdd      1.8T root  disk  brw-rw----
&#9492;&#9472;sdd1   1.8T root  disk  brw-rw----

```

And lastly, output from syslog to show that I'm not dreaming and actually have it plugged in:
```
Oct 26 11:20:47 glenn-desktop kernel: [57618.794400] usb 2-3: new high-speed USB device number 7 using ehci-pci
Oct 26 11:20:48 glenn-desktop kernel: [57618.928044] usb 2-3: New USB device found, idVendor=14cd, idProduct=1212
Oct 26 11:20:48 glenn-desktop kernel: [57618.928056] usb 2-3: New USB device strings: Mfr=1, Product=3, SerialNumber=2
Oct 26 11:20:48 glenn-desktop kernel: [57618.928063] usb 2-3: Product: Mass Storage Device
Oct 26 11:20:48 glenn-desktop kernel: [57618.928069] usb 2-3: Manufacturer: Generic
Oct 26 11:20:48 glenn-desktop kernel: [57618.928073] usb 2-3: SerialNumber: 121220160204
Oct 26 11:20:48 glenn-desktop kernel: [57618.929498] usb-storage 2-3:1.0: USB Mass Storage device detected
Oct 26 11:20:48 glenn-desktop kernel: [57618.929942] scsi10 : usb-storage 2-3:1.0
Oct 26 11:20:48 glenn-desktop mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3"
Oct 26 11:20:48 glenn-desktop mtp-probe: bus: 2, device: 7 was not an MTP device
Oct 26 11:20:49 glenn-desktop kernel: [57619.927589] scsi scan: INQUIRY result too short (5), using 36
Oct 26 11:20:49 glenn-desktop kernel: [57619.927609] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
Oct 26 11:20:49 glenn-desktop kernel: [57619.928458] sd 10:0:0:0: Attached scsi generic sg4 type 0
Oct 26 11:20:49 glenn-desktop kernel: [57620.298863] sd 10:0:0:0: [sde] Unsupported sector size 31207423.
Oct 26 11:20:49 glenn-desktop kernel: [57620.298879] sd 10:0:0:0: [sde] 0 512-byte logical blocks: (0 B/0 B)
Oct 26 11:20:49 glenn-desktop kernel: [57620.298887] sd 10:0:0:0: [sde] 31207423-byte physical blocks
Oct 26 11:20:49 glenn-desktop kernel: [57620.299735] sd 10:0:0:0: [sde] Write Protect is off
Oct 26 11:20:49 glenn-desktop kernel: [57620.299749] sd 10:0:0:0: [sde] Mode Sense: 03 00 00 00
Oct 26 11:20:49 glenn-desktop kernel: [57620.300483] sd 10:0:0:0: [sde] No Caching mode page found
Oct 26 11:20:49 glenn-desktop kernel: [57620.300495] sd 10:0:0:0: [sde] Assuming drive cache: write through
Oct 26 11:20:49 glenn-desktop kernel: [57620.304688] sd 10:0:0:0: [sde] Unsupported sector size 31207423.
Oct 26 11:20:49 glenn-desktop kernel: [57620.306512] sd 10:0:0:0: [sde] No Caching mode page found
Oct 26 11:20:49 glenn-desktop kernel: [57620.306526] sd 10:0:0:0: [sde] Assuming drive cache: write through
Oct 26 11:20:49 glenn-desktop kernel: [57620.306535] sd 10:0:0:0: [sde] Attached SCSI disk


```

Again, I appreciate the assistance.

---

### Post by sudodus on 2017-10-26
That's right, the commands I suggest do not see the micro SD card (as a mass storage device). But it seems to be connected. Maybe you can try to analyze the problem with the help of the following link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

 it is worthwhile to try according to this list,

-    Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

-    Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

-    Try other USB ports, and/or other card adapters and another computer.

-    Try another operating system (Windows, MacOS) in another computer.

-    If you still cannot

. see the drive (as a mass storage device), it is probably damaged beyond repair or

. wipe the first megabyte of the drive, and the drive is read-only, it is probably 'gridlocked', and the next stage is that it will be completely 'bricked'.

There is a limit, when you have to accept that the pendrive is damaged beyond repair, at least with tools available to normal users like you and me.

---

### Post by efflandt on 2017-10-26
What size are the microSD cards? 64 GB or larger (SDXC) would be formated as exFAT by default by the manufacturer. But exfat support is not included by default, so you need to install **exfat-utils** (which should also include **exfat-fuse** to automount).

PS: I have a USB 2.0 multi-card reader that works on any computer or laptop, **except** my main Dell XPS 8100 from 2010. It works on older Dell computers, various laptops, and even my HP PC from 2004 (which I think might be USB 1.0) which I used to install 16.04 on an SD card for my tablet PC (which only has Win7 Pro on its internal 32 GB SSD). But on my main PC there is no sign of the card reader in dmesg or anything else, like the card reader does not even power up (its LED is off). But my main PC has no trouble with USB memory sticks from 128 MB to 64 GB or a really old Lexar SD card reader.

---

