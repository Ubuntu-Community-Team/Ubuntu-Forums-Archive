---
title: "Trying to mount &amp; recover portable USB disk"
date: 2015-06-20
forum: Hardware
---

### Post by flitbee on 2015-06-20
I have a portable disk that seems to have bad sectors. I am trying to mount it in my Live Ubuntu session but it doesn't even show up. 

Doing a **demsg** gives me:

```
[ 3262.061153] [COLOR=#ff0000]Buffer I/O error on dev sdd, logical block 6, async page read[/COLOR]
[ 3442.267666] sd 6:0:0:0: timing out command, waited 180s
[ 3442.267675] sd 6:0:0:0: [sdd] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3442.267678] sd 6:0:0:0: [sdd] Sense Key : Hardware Error [current]
[ 3442.267681] sd 6:0:0:0: [sdd] Add. Sense: Internal target failure
[ 3442.267682] sd 6:0:0:0: [sdd] CDB: 
[ 3442.267684] Read(10): 28 00 00 00 00 07 00 00 01 00
[ 3442.267691] blk_update_request: I/O error, dev sdd, sector 7
[ 3442.267694][COLOR=#ff0000] Buffer I/O error on dev sdd, logical block 7, async page read[/COLOR]
[ 3442.268212] sd 6:0:0:0: [sdd] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3442.268214] sd 6:0:0:0: [sdd] Sense Key : Illegal Request [current]
[ 3442.268216] sd 6:0:0:0: [sdd] Add. Sense: Logical block address out of range
[ 3442.268217] sd 6:0:0:0: [sdd] CDB: 
[ 3442.268218] Read(10): 28 00 00 00 00 00 00 00 01 00

```

Doing **lsblk**, I don't see this drive (I assume it's sdd). Doing a **ls -l /dev/* | wc -l** before and after mounting shows a difference of 5-6 lines, so *something* is happening. I can't see /dev/sddX anywhere to run any of the disk tools. 
**lsusb** shows the device in question:
```
Bus 001 [COLOR=#0000cd]Device 014[/COLOR]: ID 0bc2:2300 [COLOR=#0000cd]Seagate[/COLOR] RSS LLC Expansion Portable
```
**usb-devices** also seems to show the device:
```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 [COLOR=#0000cd]Dev#= 14[/COLOR] Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bc2 ProdID=2300 Rev=01.30
[COLOR=#0000cd]S:  Manufacturer=Seagate [/COLOR]
S:  Product=Portable        
S:  SerialNumber=00000000    
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

Running **sudo fdisk -l** seems to hang. I have to kill the process.

But doesn't mount. What can I do? Is this the end of the road for this USB hard disk? Should I bother no more or are there ways in Ubuntu to recover this? It has a lot family photos I want to recover.

---

### Post by sandyd on 2015-06-20
```
[ 3262.061153] Buffer I/O error on dev sdd, logical block 6, async page read
[ 3442.267666] sd 6:0:0:0: timing out command, waited 180s
[ 3442.267675] sd 6:0:0:0: [sdd] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3442.267678] sd 6:0:0:0: [sdd] Sense Key : Hardware Error [current]
[ 3442.267681] sd 6:0:0:0: [sdd] Add. Sense: Internal target failure
```
These are serious errors that may or may not indicate data is recoverable.

The first thing you want to do is get the data off the disk ASAP. If the data is still recoverable, it is best to not test if the disk can endure the data recovery process without failing.

You will need another disk with enough free space to contain the erroring disk. If you don't have one now, _stop_ using the erroring disk and set it aside for now. The more disk activity there is on the erroring disk, the more chances you aren't going to be getting data back. Do _not_ ddrescue to the desktop, Ubuntu live sessions are loaded into RAM.

Then, we can install ddrescue, which is a bit better than dd in terms of recovering data from a failing disk.
```

sudo apt-get install gddrescue
sudo ddrescue -d -r3 /dev/sdd /mount/disk/test.img test.logfile
```
In the above command, "/dev/sdd" is the erroring disk, and test.img is on a new mounted disk that has enough space to store the image. test.logfile is the logfile for additional retries if there are read failures.

Start by running the commands above, and we will see where they can take us.

---

### Post by flitbee on 2015-06-20
Getting data off the disk ASAP is what I am trying to do. I do have   another disk with a larger capacity. I need to at least mount the disk   to get data off of it - I can't seem to do that. Anyway I tried to do   what you advised:

```
sudo add-apt-repository ppa:hamishmb/myppa
sudo apt-get update
sudo apt-get install ddrescue
```

I can't seem to install ddrescue now though :(. Hate it when side problems cause you to go searching for another solution :( I'll try to figure this out and do the rest.

```
ubuntu@ubuntu:~$ sudo apt-get install ddrescue
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ddrescue
```

---

### Post by sandyd on 2015-06-20
Fixed, made a typo

---

### Post by flitbee on 2015-06-20
Thank you, I figured it out too after a bit after googling:
```
sudo apt-get install [COLOR=#ff0000]g[/COLOR]ddrescue
``` and it's installed now. Do note: the command is ddresuce, package is[COLOR=#ff0000] g[/COLOR]ddrescue. 

Anyway moving forward, I ran:

```
sudo ddrescue -d -r3 /dev/sdd /media/ubuntu/PORTABLE/recovery/recovery.img recovery.log
```

Anyway I don't see anything happening. Don't see where the recovery.log  file is created too. Earlier I tried doing a disk image using the **dd**  command, but that too seemed to be doing nothing so I killed it. I have  no idea if this is running or if it's hung (like when i issue the fdisk  command). I'll leave it running for an hour and kill it if nothing  seems to be happening. 

Do advise if there's a log I can tail or any way to know if it's running or hung.

---

### Post by sandyd on 2015-06-20
Its running, dd/ddrescue has no output.

If your disk is badly damaged, dd/ddrescue will take longer than normal due to it retrying the read a few times before indicating it is a failure

---

### Post by flitbee on 2015-06-20
thanks sandy. I'll leave it for half a day. Hope I get something out of it. I only ask because** fdisk -l** hangs and I couldn't see the partition for the device (e.g. sdd1) anywhere. I'll report back in a few hours. Fingers crossed.

UPDATE (after an hour and a half of no activity I see: )

```
GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:         0 B,  errsize:    131 kB,  current rate:        0 B/s
   ipos:    327680 B,   errors:       2,    average rate:        0 B/s
   opos:    327680 B, run time:       3 m,  successful read:       3 m ago
Copying non-tried blocks... Pass 1 (forwards)
```

Another UPDATE:
```
GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:         0 B,  errsize:    131 kB,  current rate:        0 B/s
rescued:         0 B,  errsize:   7274 kB,  current rate:        0 B/s
   ipos:   105233 MB,   errors:     111,    average rate:        0 B/s ago
   opos:   105233 MB, run time:    5.55 h,  successful read:    5.55 h ago
Copying non-tried blocks... Pass 1 (forwards)
```



The recovery.log has:

```
ubuntu@ubuntu:~$ more recovery.log 
# Rescue Logfile. Created by GNU ddrescue version 1.19
# Command line: ddrescue -d -r3 /dev/sdd /media/ubuntu/PORTABLE/recovery/recover
y.img recovery.log
# Start time:   2015-06-21 13:01:09
# Current time: 2015-06-21 13:04:13
# Copying non-tried blocks... Pass 1 (forwards)
# current_pos  current_status
0x00020000     ?
#      pos        size  status
0x00000000  0x00010000  *
0x00010000  0x00010000  ?
0x00020000  0x00010000  *
0x00030000  0x1FFFFFCFE00  ?


```

---

### Post by flitbee on 2015-06-21
> **sandyd said:**
> [code][ 3262.061153] 

The first thing you want to do is get the data off the disk ASAP. If the data is still recoverable, it is best to not test if the disk can endure the data recovery process without failing.

You will need another disk with enough free space to contain the erroring disk. If you don't have one now, _stop_ using the erroring disk and set it aside for now. The more disk activity there is on the erroring disk, the more chances you aren't going to be getting data back. Do _not_ ddrescue to the desktop, Ubuntu live sessions are loaded into RAM.

Then, we can install ddrescue, which is a bit better than dd in terms of recovering data from a failing disk.....................


Just noticed this at [http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)
It says:

> Never try to repair a file system on a drive with I/O errors; you will probably lose even more data.

If that is true, does that mean I shouldn't be running it on my disk?

---

### Post by sudodus on 2015-06-21
1. The way to do it is the way you are doing it - ***clone the failing drive with ddrescue***.

2. After the cloning has finished (and no more failing sectors can be recovered), you can start to ***recover files from the cloned copy***.

-o-

The 'built-in tutorial' in ```
info ddrescue
``` is well written, and will help you. I read it twice in order to understand it, and after that I can save all or almost all data from failing disks :-)

---

### Post by flitbee on 2015-06-22
Ok, anyway am way into it to pull back now :) 
Here's an update: I had to shut down my PC. I saved the log file off as that is needed to recommence the recovery (else it will start from the beginning). Once I started my Live CD image, i found the device name give to the USB via **dmesg** and I see it was not /dev/sdc

So I reissued the recovery command as:
```

sudo ddrescue -d -r3 -vvvv /dev/sdc /media/ubuntu/PORTABLE/recovery/recovery.img /media/ubuntu/PORTABLE/recovery.log 
```

An update: It's been 2 days since I issued the command I don't see any progress except for my recovery.log file being updated every 5 mins or so. I uaased this command to parse the log file:

```
ddrescuelog -t recovery.log
```

It gives me the following output:

```
current pos:     1087 GB,  current status: copying
domain size:     2199 GB,  in 2000 area(s)
rescued:         0     B,  in    0 area(s)  (  0%)
non-tried:       2198  B,  in 1040 area(s)  ( 99.99%)

errsize:        68157 kB,  errors:   1040   (  0.00%)
non-trimmed:    68157 kB,  in 1040 area(s)  (  0.00%)
non-split:           0 B,  in    0 area(s)  (  0%)
bad-sector:          0 B,  in    0 area(s)  (  0%)
```

I don't know to read this (despite googling). Does this mean anything is happening? Or even what % this is at? This is a 300GB HDD, but I'm not sure what % this is at. 
[LIST=1]
[*]Is anything being recovered? "rescued = 0B" --> That isn't good is it? Do I need to still persist with this? 
[*]Does (current pos)/(domain size) give a % of how far this phase has completed?
[*] current status: copying --> Copying what? I don't see anything being copied (to the *.img file)
[*]non-tried = 99.99% --> Does this mean 99% of the drive hasn't been "scanned" ? 
[/LIST]

---

### Post by flitbee on 2015-06-24
2 days on and still no change. I've updated the [post ]("http://ubuntuforums.org/showthread.php?t=2283303&p=13308032#post13308032")before this with the status. Any help to my comments above would be appreciated.

---

### Post by sudodus on 2015-06-24
I think it does not work. It seems that it cannot transfer some data, and I can only guess why. It might be a worst case, that the drive is failing completely, but it is worth trying to start it again (in the same or similar way). ddrescue is a good tool, I think you need to go to an expensive professional method to get something that is better.

---

### Post by flitbee on 2015-06-27
Yes I give up. There's no way I can get this to work :(

---

### Post by smolny on 2016-03-07
> **flitbee said:**
> Yes I give up. There's no way I can get this to work :(

If you still own the drive, there is a MMHD tool. AFAIR, the executable is for windows (or dos even), but I managed to recover data from a 40GB HDD that was not even recognized by BIOS. Have made a bootable cd-r, then cloned whatever possible to another disk, and only then recovered files from a failing disk's image. Cloning alone took almost a week, so I did it on an oldish motherboard. Recovered almost all file(names), but some files were corrupted. Still worth trying. Good luck.

---

### Post by uconnkoala on 2017-01-16
I had similar issues when trying to mount an 8TB Western Digital USB MyBook hard drive. This is an older Supermicro server, but I also had issues on my newer ThinkPad, and had to plug it into the USB 2.0 slot on the laptop.

I ended up plugging a USB hub into the server, and then the external hard drive into the hub. Everything seemed to work ok after that.

```
[1246034.762336] usb 2-1.4: Product: My Book 25EE
[1246034.762339] usb 2-1.4: Manufacturer: Western Digital

[1245287.375388] Buffer I/O error on dev dm-2, logical block 786431, async page read
[1245294.312820] Buffer I/O error on dev dm-2, logical block 44, lost async page write

```

---

### Post by fundix on 2017-01-19
> **uconnkoala said:**
> I had similar issues when trying to mount an 8TB Western Digital USB MyBook hard drive. This is an older Supermicro server, but I also had issues on my newer ThinkPad, and had to plug it into the USB 2.0 slot on the laptop.  I ended up plugging a USB hub into the server, and then the external hard drive into the hub. Everything seemed to work ok after that.  ```
[1246034.762336] usb 2-1.4: Product: My Book 25EE [1246034.762339] usb 2-1.4: Manufacturer: Western Digital  [1245287.375388] Buffer I/O error on dev dm-2, logical block 786431, async page read [1245294.312820] Buffer I/O error on dev dm-2, logical block 44, lost async page write 
```  I resolve disk problem - I bought SATA to USB box with 2 docks and with clone function ... I connected disks and let it clonning after 5days I have clonned 680G from 2TB disk. Disk is broken but some data I have on new drive and I try R-studio software and recovered some files ... It's for long nights but it possible get some data back. Backup is better way :-)

---

