---
title: "Grub issues with Fake Raid"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by PCFascist on 2009-05-14
I've followed this howto: 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Here is where I run into issues:
```
root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/via_ceedgdabjh2
device (hd0) /dev/mapper/via_ceedgdabjh2
grub> find /boot/grub/stage1
find /boot/grub/stage1
Unknown partition table signature

Error 15: File not found
grub> 
```


I've taken the liberty of running the following troubleshooting script that seems to be asked for in most grub troubleshooting threads... 
boot_info_script032:
```

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50e350e3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           1,879,605   302,584,274   300,704,670  83 Linux
/dev/sdb2    *             63     1,879,604     1,879,542  83 Linux
/dev/sdb3         302,584,275   312,592,769    10,008,495  82 Linux swap / Solaris

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb3 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/mapper/via_ceedgdabjh1: LABEL="/" UUID="2b1e8cb6-3ebc-4a82-a3f2-de5a8aeac4c9" TYPE="ext3" 
/dev/mapper/via_ceedgdabjh2: LABEL="/boot" UUID="43e5eeea-f682-4b9a-8cfa-5782d8fcfa82" TYPE="ext3" 
/dev/mapper/via_ceedgdabjh3: UUID="7c112c46-96b8-4eb6-87d3-49180a1692c6" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/mapper/via_ceedgdabjh1 on /target type ext3 (rw)
/dev/mapper/via_ceedgdabjh2 on /target/boot type ext3 (rw)
/dev on /target/dev type none (rw,bind)
proc on /target/proc type proc (rw)
sys on /target/sys type sysfs (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
```

I had to create my device.map file
 nano /boot/grub/device.map:
```

hd0 /dev/mapper/via_ceedgdabjh2
hd1 /dev/mapper/via_ceedgdabjh1
hd2 /dev/mapper/via_ceedgdabjh3
```

I've confirmed that the second volume is my boot partition on the dmraid from gparted.

Thanks in advance for any help!

---

### Post by PCFascist on 2009-05-14
hah! I feel dumb I was specifying a partition in my device.map, I needed to give the entire drive~!

I changed the device.map to
```

hd0 /dev/mapper/via_ceedgdabjh
``` 

I was then able to run find /boot/grub/stage1
```
grub> device (hd0) /dev/mapper/via_ceedgdabjh
device (hd0) /dev/mapper/via_ceedgdabjh
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> 

```

---

### Post by PCFascist on 2009-05-14
Now this ended in a error 17 when I try to boot...

Regardless of boot order of the drives...


I had two different grub folders at this point on the drive. I deleted one of them...

---

### Post by PCFascist on 2009-05-15
If i change the bios to 'raid' my drives I then get and error 15. I can run find /boot/grub/stage1 and run the root,setup commands from the grub prompt, I get no change when I boot.

When I boot into the live cd I see that my 1st partition is still there. (which I had made for /boot, but since I was still having issues I thought I'd just move boot to the root partition.)
I've deleted it now and will run grub setup...

---

### Post by PCFascist on 2009-05-15
Hrm, looks like I've neglected to run the following command after running grub setup

```
update-initramfs -u
```

This allowed me to not get any errors from grub and once I added pci=nomsi to my boot line I was able to start launching linux and it failed when it tried to grab the image off of /dev/hdb1 which I don't have...

Booting back into the Live CD.

Adding rmraid to my /etc/initramfs-tools/modules file and running the initramfs update again... allowed me to boot when I also changed the menu.lst file to point to the /dev/mapper/via_uuid

I got a failed ext3 check as it was unable to find a UUID device, but who cares it boots!

---

### Post by haider_up32 on 2009-08-15
mhk@mhk-desktop:~$ ls -l /dev/mapper
total 0
crw-rw---- 1 root root  10, 61 Aug 16  2009 control
brw-rw---- 1 root disk 252,  0 Aug 15 20:50 isw_feacijab_Volume0
brw-rw---- 1 root disk 252,  1 Aug 15 20:50 isw_feacijab_Volume01
brw-rw---- 1 root disk 252,  2 Aug 15 20:50 isw_feacijab_Volume02


i have recently made a raid array .** i just need to mount on ubuntu 9.04** . i have installed dmraid ..what to do next?? Ubuntu is installed on non-raid disk.

---

### Post by haider_up32 on 2009-08-15
dmraid -r
/dev/sdc: isw, "isw_feacijab", GROUP, ok, 976773166 sectors, data@ 0
/dev/sdb: isw, "isw_feacijab", GROUP, ok, 976773166 sectors, data@ 0

---

### Post by haider_up32 on 2009-08-16
How shud i mount partition created in raid arrays?? it is recognised by dmraid 

```

root@mhk-desktop:/home/mhk# sudo dmraid -ay
RAID set "isw_feacijab_Volume0" already active
RAID set "isw_feacijab_Volume01" already active
RAID set "isw_feacijab_Volume02" already active

root@mhk-desktop:/home/mhk# sudo fdisk /dev/mapper/isw_feacijab_Volume0

The number of cylinders for this disk is set to 121602.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p 

Disk /dev/mapper/isw_feacijab_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb36a5ff6

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_feacijab_Volume0p1   *           1         893     7172991    7  HPFS/NTFS
/dev/mapper/isw_feacijab_Volume0p2             894        1786     7173022+   7  HPFS/NTFS

Command (m for help): 


root@mhk-desktop:/home/mhk# dmraid -s
*** Group superset isw_feacijab
--> Active Subset
name   : isw_feacijab_Volume0
size   : 1953536512
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
```

---

