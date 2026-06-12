---
title: "unable to mount NEW VOLUME"
date: 2009-05-20
forum: Hardware
---

### Post by Santooka on 2009-05-20
i am trying to mount a disk partition NEW VOLUME and here's what i get:

> fadythebassist@fadythebassist-desktop:~$ sudo mount /dev/sda5 /media/testing
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

i tried ntfsfix and here's what i got:

> fadythebassist@fadythebassist-desktop:~$ sudo ntfsfix /dev/sda5
Mounting volume... pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Remount failed: Input/output error.

here's my /etc/mtab:

> /fadythebassist@fadythebassist-desktop:~$ cat /etc/mtab
/dev/sda3 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-12-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/fadythebassist/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=fadythebassist 0 0
/dev/sr0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=fadythebassist 0 0
/dev/sda5 /media/testing unknown rw 0 0
0

here's my /etc/fstab:

> fadythebassist@fadythebassist-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=aad6942f-9313-4c1b-8625-1e267eb0d28e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=385d1afb-1a27-45ad-84c9-4f7384a45668 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


i used to have this problem with ubuntu 8.10 now i changed to 9.04 and still the same.

so is there any one to help me to fix it?

i did chckdsk /f on windows and restarted twice like i read the alarm and nothing happened

here' my fdisk -l:

> fadythebassist@fadythebassist-desktop:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f114f10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10198    81914614    7  HPFS/NTFS
/dev/sda2           10199       73974   512280720    f  W95 Ext'd (LBA)
/dev/sda3           73975       77621    29294527+  83  Linux
/dev/sda4           77622       77825     1638630   82  Linux swap / Solaris
/dev/sda5           10199       48443   307202374+   7  HPFS/NTFS
/dev/sda6           48444       73974   205077726    7  HPFS/NTFS


and here's blkid:

> fadythebassist@fadythebassist-desktop:~$ blkid
/dev/sda1: LABEL="DISK2PART1" UUID="7D6D-175E" TYPE="vfat" 
/dev/sda3: UUID="aad6942f-9313-4c1b-8625-1e267eb0d28e" TYPE="ext3" 
/dev/sda4: UUID="385d1afb-1a27-45ad-84c9-4f7384a45668" TYPE="swap" 
/dev/sda5: UUID="54DC4056DC403510" LABEL="NEW VOLUME" TYPE="ntfs" 
/dev/sda6: UUID="184A5B374A5B113C" LABEL="New Volume 2" TYPE="ntfs"

i guess these are all the info that i could think of....

PLEASE HELP!!!!


I AM SICK OF WORKING ON WINDOWS VISTA!!!!!

---

### Post by Santooka on 2009-05-20
is it that hard?

anyone please help?

---

### Post by jasone on 2009-05-20
Ok my question is propably really stupid cause i'm a complete noob but you have installed ntfs-3g right?
I'm sorry if this a stupid question.

---

### Post by Santooka on 2009-05-20
well it's not stupid at all, i am a complete noob myself!

i searched and found that ntfs-3g is intalled properly.

---

### Post by Santooka on 2009-05-20
bump

---

### Post by unclejac on 2009-05-21
ok so i guess you need to add the drive NEW VOLUME to your fstab.

it doesn't appear to be there. so you have to add it manually by editing the fstab.

from the terminal use the following:

```
sudo gedit /etc/fstab
```

then after a quick read and using some info from:

 [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

 you should be able to figure out the line to add to your fstab. 

This page helped me a while back, explains a load of possibilities for your fstab. 

Hope this helps ;)

---

### Post by Santooka on 2009-05-21
thank you for your help, but there's something, that not all my partitions are listed in the /etc/fstab and i can mount them normally..... what i know about the /etc/fstab file is -please correct me if i am wrong - that it mounts the partition automatically while booting the system.... so i don't know, anyways i am at work right now i will try editing the file when i get home.

and thanks ;)

---

### Post by unclejac on 2009-05-21
Hi yeah thats correct the fstab does some donkey work for you and mounts your drives while your system is booting up

If your like me and forever changing system setup / moving drives around or simply want to make an addition because you bought a shiny new hard drive. Then I guess its worth learning a bit about the FSTAB

Once you perfect it your laughing and wonder what all the fuss was about ;)

Anyway give it a go and let us know how you get on . . .

---

### Post by dE_logics on 2010-04-21
And in reality the problem never got fixed....


And there doesn't seem to be a crack for it...

---

