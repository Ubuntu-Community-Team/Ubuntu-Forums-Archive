---
title: "PLEASE help setting up fakeraid array sil3114"
date: 2009-09-11
forum: Hardware
---

### Post by drseung on 2009-09-11
Hi all

Can someone please help me with this. I am new to this and have been tearing my hair out trying to figure out why dmraid does not recognise my sil3114 fakeraid as a single device.

This is the setup I have
1 80G IDE on which the ubuntu installation is.
A RAID10 array (configured at the bios) with 4 500GB disks.

Ubuntu 9.04 server boots up fine (kernel 2.6.28-11-server) I run dmraid -r 

**dmraid -r**[INDENT]/dev/sdd: sil, "sil_ajajbgahfgdd-1", stripe, ok, 1951442944 sectors, data@ 0
/dev/sdc: sil, "sil_ajajbgahfgdd-1", stripe, ok, 1951442944 sectors, data@ 0
/dev/sdb: sil, "sil_ajajbgahfgdd-0", stripe, ok, 1951442944 sectors, data@ 0
/dev/sda: sil, "sil_ajajbgahfgdd-0", stripe, ok, 1951442944 sectors, data@ 0
[/INDENT]**dmraid -ay**[INDENT]RAID set "sil_ajajbgahfgdd-1" was not activated
[/INDENT]**ls -lrt /dev/mapper**[INDENT]total 0
crw-rw---- 1 root root 10, 61 2009-09-10 14:39* control*
[/INDENT]viewing the /var/log/messages this is what I c

**cat /var/log/messages**[INDENT] Sep 11 02:04:46 BISON-NAS kernel: [41111.942869] device-mapper: table: device /dev/sdc too small for target
Sep 11 02:04:46 BISON-NAS kernel: [41111.942919] device-mapper: ioctl: error adding target to table
[/INDENT]Any thoughts why I get nothing in the /dev/mapper. Thanks for taking a look.

---

### Post by drseung on 2009-09-11
Still debugging this .... here is the output from my dmraid -vvv -dd -ay

Here is to hoping it rings a bell to someone.

**dmraid -vvv -ddd -ay**
[INDENT]WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sde: asr     discovering
NOTICE: /dev/sde: ddf1    discovering
NOTICE: /dev/sde: hpt37x  discovering
NOTICE: /dev/sde: hpt45x  discovering
NOTICE: /dev/sde: isw     discovering
NOTICE: /dev/sde: jmicron discovering
NOTICE: /dev/sde: lsi     discovering
NOTICE: /dev/sde: nvidia  discovering
NOTICE: /dev/sde: pdc     discovering
NOTICE: /dev/sde: sil     discovering
NOTICE: /dev/sde: via     discovering
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdd: sil metadata discovered
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdc: sil metadata discovered
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sda: sil metadata discovered
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching sil_ajajbgahfgdd-1
DEBUG: _find_set: not found sil_ajajbgahfgdd-1
DEBUG: _find_set: searching sil_ajajbgahfgdd
DEBUG: _find_set: not found sil_ajajbgahfgdd
DEBUG: _find_set: searching sil_ajajbgahfgdd-1
DEBUG: _find_set: not found sil_ajajbgahfgdd-1
NOTICE: added /dev/sdd to RAID set "sil_ajajbgahfgdd"
DEBUG: _find_set: searching sil_ajajbgahfgdd-1
DEBUG: _find_set: searching sil_ajajbgahfgdd-1
DEBUG: _find_set: found sil_ajajbgahfgdd-1
DEBUG: _find_set: found sil_ajajbgahfgdd-1
DEBUG: _find_set: searching sil_ajajbgahfgdd
DEBUG: _find_set: found sil_ajajbgahfgdd
DEBUG: _find_set: searching sil_ajajbgahfgdd-1
DEBUG: _find_set: found sil_ajajbgahfgdd-1
NOTICE: added /dev/sdc to RAID set "sil_ajajbgahfgdd"
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: not found sil_ajajbgahfgdd-0
DEBUG: _find_set: not found sil_ajajbgahfgdd-0
DEBUG: _find_set: not found sil_ajajbgahfgdd-0
DEBUG: _find_set: searching sil_ajajbgahfgdd
DEBUG: _find_set: found sil_ajajbgahfgdd
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: not found sil_ajajbgahfgdd-0
NOTICE: added /dev/sdb to RAID set "sil_ajajbgahfgdd"
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: found sil_ajajbgahfgdd-0
DEBUG: _find_set: found sil_ajajbgahfgdd-0
DEBUG: _find_set: searching sil_ajajbgahfgdd
DEBUG: _find_set: found sil_ajajbgahfgdd
DEBUG: _find_set: searching sil_ajajbgahfgdd-0
DEBUG: _find_set: found sil_ajajbgahfgdd-0
NOTICE: added /dev/sda to RAID set "sil_ajajbgahfgdd"
DEBUG: checking sil device "/dev/sdc"
DEBUG: checking sil device "/dev/sdd"
***DEBUG: set status of set "sil_ajajbgahfgdd-1" to 16***
DEBUG: checking sil device "/dev/sda"
DEBUG: checking sil device "/dev/sdb"
[I][B]DEBUG: set status of set "sil_ajajbgahfgdd-0" to 16
DEBUG: set status of set "sil_ajajbgahfgdd" to 16[/B][/I]
***RAID set "sil_ajajbgahfgdd-1" was not activated***
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "sil_ajajbgahfgdd-1"
DEBUG: freeing device "sil_ajajbgahfgdd-1", path "/dev/sdc"
DEBUG: freeing device "sil_ajajbgahfgdd-1", path "/dev/sdd"
DEBUG: freeing devices of RAID set "sil_ajajbgahfgdd-0"
DEBUG: freeing device "sil_ajajbgahfgdd-0", path "/dev/sda"
DEBUG: freeing device "sil_ajajbgahfgdd-0", path "/dev/sdb"
DEBUG: freeing devices of RAID set "sil_ajajbgahfgdd
[/INDENT]

---

### Post by ronparent on 2009-09-13
I am too unfamiliar with setup of fakeraid raid10's to be of definitive help. Looking at what you presented in your first post I get the impression that you are seeing what you should see if the 1Tb raid10 is unformatted. If it _is_ unformatted, have you tried looking at it in gparted. If everything is ok gparted should show a raid drive with 1Tb of unallocated space (as well as four 500Gb drives with unallocated space - these 500Gb drives must be ignored). If that were to be the case you would be all set to create whatever partitions you wanted. 

To explain a bit. If you look in **man dmraid** your output of dmraid -r looks very like the example the man pages provide for a raid10 setup. Have your tried **ls /dev/mapper**? The output would show if and what symbolic links had been created by sudo dmraid -ay. If nothing shows in /dev/mapper then we would have to keep looking for more answers!

---

### Post by drseung on 2009-09-14
ronparent -- Thanks for taking a look at this. You are right that the drivers are not partitioned. Also my /dev/mapper folder is empty, so when I run "**ls -lrt /dev/mapper**" the output is simplly.
[INDENT][INDENT]*total 0*
*crw-rw---- 1 root root 10, 61 2009-09-10 14:39 control*
[/INDENT][/INDENT]Now I did take a look using Gparted as you suggested but it shows me 4 seperate drives. (*I should point out that this is a server and I temporarily instualled ubuntu desktop "no frills" to troubleshoot this <-- desperate I am*)
 
When use this setup in a raid1 or raid0 or raid 5 configuration everything seems to work fine.
 
Could it be that RAID10 is not supported for silicon image 3114 [sil format handler in dmraid -l] or there is a bug with it?

---

### Post by ronparent on 2009-09-14
I believe it's supported. If you run **sudo dmraid -l** the output lists supported formats by name and numbers for raids supported. If it doesn't work for a raid10 it is possible that the sil raid10 specs have changed without a corresponding update in dmraid? However your posting of **dmraid -vvv -ddd -ay** indicates that all four devices have been added to sil_ajajbgahfgdd. That is followed with "freeing of devices in sil_ajajbgahfgdd" which I don't understand. You might inquire at the dmraid site for the status of raid10 in sil. Otherwise from that you seem to be doing all the right things and the lack of results is puzzling. By the way, what is your output of **sudo dmraid -b** when the raid bios is set for raid10?

---

### Post by drseung on 2009-09-14
Running dmraid -b in a RAID10 configuration looks like this.
 
**dmraid -b**
[INDENT]/dev/sde:    156301488 total, "WD-WMAM9KJ47889"
/dev/sdd:    976773168 total, "6QG0GLYE"
/dev/sdc:    976773168 total, "9QG2M00M"
/dev/sdb:    976773168 total, "9QG2Y979"
/dev/sda:    976773168 total, "9QG2WZX4"

[/INDENT]I also ran dmraid -rD to get the metadata but I do not have a tool to inspect the output. Do you know of any tool I can us to review this xxx.dat files?
 
By the way **/dev/sde** is the primary IDE it is attached to an onboard Serial ATA configured to work as IDE. It is where the filesystem is loaded and not a part of the raid array.

---

### Post by ronparent on 2009-09-14
The -b option further confirms that dmraid is not adding your four drives to a raid array. If you haven't already done so I might suggest: 
1) removing the raid drives from raid in raid bios 
2) turning off raid in your main bios 
3) using **dmraid -E** to erase all metadata on the drives
Then reversing the process:
4) turning the raid bios back on in your main bios
5) entering the raid bios a setting up the raid10 again - if raid10 is an option in bios we should assume sil can handle raid10; this will also write new metadata and assign a new raid id to the metadata area.
6) Try again to activate the array with **dmraid -ay**

I frankly am at a loss what is going on. Maybe by systematically repeating these steps (if you haven't tired of it) we can establish a new raid10 from scratch. If this works, the new raid_id should appear in gparted.

I don't know what format the metadata is in. I'll try to research it on a computer I have sitting idle with a raid0 set in it.

---

### Post by drseung on 2009-09-17
Thanks for the suggestion, I am stumped I tried as you suggested here but no change. 

So I am throwing in the towel.

I am going to settle with RAID1 on this box as this is the highest priority.

Not sure what is happening here but Something wrong with this silicon image. I used a isw based card I had on another box everything seems to work fine.

I am tempted however to try to stripe (RAID0) the identified dmraid1 devices using LVM.

Would this work?

---

### Post by ronparent on 2009-09-17
The main danger with raid0 is that there is no redundancy. The performance advantages make it attractive for OS use. I would personally be reluctant to use raid0 for data without a comprehensive backup plan. I personally have two 160Gb drives configured as raid0 for instamce. I plan on transfering them to my main unit, reformating them (necessary because of a diferent MB raid chipset), and, using them to install win xp, ubuntu and win7 when released. My data meanwhile would continue to reside on a non-raid drive with a backup scheme to distribute copies between another fixed drive, an external drive, and, various network drives. 

Your decision to abandon the raid10 solution cannot be faulted - there is no use barking up against an intractable problem. I Sil the only raid chipset on the MB? I only ask because I have an Asus MB with both sil and nvidia.

---

### Post by drseung on 2009-09-17
Good advice, I think it was the effects of dehydration when for a fleeting moment thoughts of RAID0 wondered through my mind in this case [laying off the coffee now ...well, for today].

Indeed Sil is the only chip on the MB. Kinda sucks but this is to be strictly a NAS device and the mirrored approach is the other alternative here [compromise on the write speed, but will see how it goes].

Hopefully the rest will be painless.

---

