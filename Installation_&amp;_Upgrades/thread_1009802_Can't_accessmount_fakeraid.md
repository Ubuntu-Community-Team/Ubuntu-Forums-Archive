---
title: "Can't access/mount fakeraid"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by toldert on 2008-12-13
I have been following the tutorials and I have solved my dualboot issues.  Now, I just need to access my Windows (fake)raid-0 drive. 

The first set of instructions I ran across walked me through what I now understand to be a software raid setup using mdadm.  I was able to build the array with this, but not able to get it to mount.  I then found the instructions for using dmraid.  I ran dmraid -s, then with -r then with -ay.   I get no response on screen with -ay.  It doesn't seem to do anything.  I think I am doing the right things now, but am concerned that I messed something up with the mdadm command.  

My raid drive (70Gb) has two partitions.  On is my windows boot, and the other is my windows programs and data.  Ubuntu is loaded on a 30Gb partition on the 250Gb drive (1Gb swap, 15Gb Fat32)

I am including the log of my terminal below.  

Troy



troy@troy-desktop:~$ **sudo apt-get install mdadm**
[sudo] password for troy: 

**CLIP download and install

troy@troy-desktop:~$ **cat /proc/partitions**
major minor  #blocks  name

   8     0   39082680 sda
   8     1   20972826 sda1
   8     2   57183367 sda2
   8    16   39082680 sdb
   8    32    6347880 sdc
   8    48  244198584 sdd
   8    49  199286293 sdd1
   8    50          1 sdd2
   8    51   29294527 sdd3
   8    53     971869 sdd5
   8    54   14643184 sdd6
troy@troy-desktop:~$ **sudo mdadm --build /dev/md0 --chunk=64 --level= --raid-devices=2 /dev/sda /dev/sdb**
mdadm: invalid raid level: 
troy@troy-desktop:~$ **sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda /dev/sdb**
mdadm: array /dev/md0 built and started.
troy@troy-desktop:~$ **sudo mkdir /media/Windows**
troy@troy-desktop:~$ **sudo mount -t ntfs /dev/md0 /media/Windows**
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
troy@troy-desktop:~$ **sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb /dev/sda**
mdadm: SET_ARRAY_INFO failed for /dev/md0: Invalid argument
troy@troy-desktop:~$ **cat /proc/mdstat**
Personalities : [raid0] 
md0 : active raid0 sdb[1] sda[0]
      78165248 blocks super non-persistent 64k chunks
      
unused devices: <none>
troy@troy-desktop:~$ **sudo dmraid -s**
sudo: dmraid: command not found
troy@troy-desktop:~$ 
troy@troy-desktop:~$ **sudo apt-get install dmraid**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdmraid1.0.0.rc14
The following NEW packages will be installed:
  dmraid libdmraid1.0.0.rc14
0 upgraded, 2 newly installed, 0 to remove and 157 not upgraded.

**CLIP download and install

troy@troy-desktop:~$ **sudo dmraid -s**
*** Set
name   : via_bhbaaifedc
size   : 156330496
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
troy@troy-desktop:~$ **sudo dmraid -r**
/dev/sdb: via, "via_bhbaaifedc", stripe, ok, 78165359 sectors, data@ 0
/dev/sda: via, "via_bhbaaifedc", stripe, ok, 78165359 sectors, data@ 0
troy@troy-desktop:~$ **sudo dmraid -ay**
troy@troy-desktop:~$ **sudo dmraid -ay**
troy@troy-desktop:~$ **sudo dmraid**
ERROR: No arguments/options given (-h for help)

troy@troy-desktop:~$ **sudo dmraid -h**
dmraid: Device-Mapper Software RAID tool

**CLIP 

troy@troy-desktop:~$

---

### Post by toldert on 2008-12-16
Ok, I don't know if I have missed something in the directions I am following, or if I have not searched hard enough.  

I think I have read and followed explicitly, and I don't know how to be any more thorough in my search.  

The only thing I can see that would have things messed up with mdadm so that dmraid cannot mount the raid drive.  I ran: cat /proc/mdstat  and got:

[INDENT]Personalities : [raid0]
md0 : active raid0 sdb[1] sda[0]
78165248 blocks super non-persistent 64k chunks[/INDENT]

Do I need to do something to reverse what has been done with mdadm so that I can mount the raid setup with dmraid?  

This is fakeraid with a VIA chipset.

---

