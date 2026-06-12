---
title: "External Hard Drive Major Annoyance"
date: 2008-11-13
forum: Hardware
---

### Post by aeronotix on 2008-11-13
I know you will have seen many a thread about external hard drives but please bear with me, I've literally spent about 4 hours trying to get it going.

It's a Freecom 400GB external USB hard drive.

It has worked on Ubuntu before (albeit a bit flaky) which is what is the most annoying thing to me. lsusb doesn't list it as being connect, fdisk -l doesn't show anything up about the drive.

It's there in when I boot into windows, but not in Ubuntu. I've tried the "safely remove hardware" within windows, clean shutdown and still no External hard drive. Would really appreciate any tools or tips you can pass along. It's the main reason I'm still having to go back to Windows.

---

### Post by cariboo on 2008-11-13
What is the output of dmesg when you plug the device in? 

type in a terminal:

```
dmesg
```

You should see something like this, if your drive is working correctly:

```
[ 7715.374615] sd 4:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[ 7715.374832] sd 4:0:0:0: [sdc] Write Protect is off
[ 7715.374838] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 7715.375142] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7715.375411]  sdc: sdc1 sdc2
[ 7715.419450] sd 4:0:0:0: [sdc] Attached SCSI disk
[ 7715.419745] sd 4:0:0:0: Attached scsi generic sg3 type 0
```

Note: the above is for an eSata drive but the output should be the same for a usb device.

Jim

---

### Post by aeronotix on 2008-11-13
This is the output for dmesg, think this the part you'd want to see. 

```
  48.934133] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   48.941145] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   48.948129] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   48.955108] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   48.967156] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   48.967201] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   48.978143] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   48.978188] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   48.989132] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   48.989179] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   49.000114] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   49.000160] sd 4:0:0:3: Attached scsi generic sg5 type 0

```

Also the output for lsusb does have what looks like it may be attached to the hard drive, maybe it is?

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 15ca:00c3  
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1241:1503 Belkin 
Bus 001 Device 001: ID 0000:0000
```

Particularly the part that says Bus 002 Device 003: ID 15ca:00c3 but doesn't have a literal name like the rest of them, maybe that tells you guys something?

---

### Post by aeronotix on 2008-11-17
bump

---

### Post by vanadium on 2008-11-17
To me, it looks as if the drive is normally connected. Are you sure you executed fdisk as root?

---

### Post by aeronotix on 2008-11-17
Yeah I typed in ```
sudo fdisk -l
```

And all I got was the internal hard drive information.

What do you think about that lsusb thing? Because that looks like something is connected, I tried this drive in my friends Laptop last night running LinuxMINT and it ran perfectly fine.

---

### Post by Bucky Ball on 2008-11-17
Try;

**sudo blkid**

... and see if it shows.

Could you post the result of that and **fdisk -l **please. Does the drive have a name in Windoze, or is it just 'Drive M' or something generic? Have you labelled it?

---

### Post by aeronotix on 2008-11-17
I don't think it does, unless it's me not understanding, I'll paste it in. Thanks for helping!

```
/dev/sda1: UUID="C0BC4183E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="5E002008001FE635" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="051a02bd-d608-4291-b09c-c58ff37ae656" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="79b94f5d-86bb-4770-839f-ea35a92f46ec" 
/dev/sda6: UUID="f9e12426-0382-45c3-aca8-77ca3aa83dfc" TYPE="ext3" 
```

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa325a97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10383       17474    56957952   83  Linux
/dev/sda4           17474       20023    20474843    f  W95 Ext'd (LBA)
/dev/sda5           17475       17595      971932+  82  Linux swap / Solaris
/dev/sda6           17596       20023    19502878+  83  Linux

```

---

### Post by Bucky Ball on 2008-11-17
Okay, can you account for these devices? And what is the external drive formatted in? Is that NTFS? If so, it would be coming up as 'Acer' or '
PQSERVICE', which it probably already does. Which leaves sda3 and sda6, both EXT3 partitions/discs.
Both unlabelled. One will contain Ubuntu, what is the other? (probably sda6)

---

### Post by aeronotix on 2008-11-17
I have a Windows partition that comes up with Acer, and another recovery partition that comes up with PQSERVICE. Recovery partition because I didn't get a recovery disk.

sda6 is just another partition that I formatted to ext3 to use with Ubuntu, you're right the other has Ubuntu. To be honest it looks a mess because I fudged up the partitions at install, but this is a completely separate hard drive.

Sorry to someone above, yes in windows it's called FREECOM L:

---

### Post by Bucky Ball on 2008-11-17
Yea, it's really not there! How odd. That has me stumped but I'll keep thinking ...

---

### Post by aeronotix on 2008-11-17
Thanks!I'll keep this bumped over the next few days then.

---

### Post by aeronotix on 2008-11-17
UPDATE: I found a file in /usr/src/linux-headers-2.6.24-21-generic/include/config/usb/storage called freecom.h

My drive that I'm trying to use is called Freecom, does this mean anything? Or could it be from when the drive WAS originally working? What if I remove this file and then plug the drive back in? Also when I sudo gedit that file is blank, is there any code I could put in it to make it auto-mount? Presuming this file has something to do with the drive.

---

### Post by aeronotix on 2008-11-17
Well it's fixed now, I found some code to put into the blank freecom.h file but this isn't what may have fixed it. I went back into windows and safely removed hardware and then shut down instead of restarted and it was right there on the desktop when I booted into Ubuntu. Oh well, the joys of a new OS.

---

### Post by boof1988 on 2008-11-17
Glad it's now working for you.  I'm trying to learn how to label, mount drives and stuff and it's a pretty good challenge for now.

:guitar:

---

### Post by psusi on 2008-11-17
The section of dmesg you pasted appears to pertain to your 8 in 1 memory card reader, not the usb hard disk.

---

### Post by Bucky Ball on 2008-11-17
> **aeronotix said:**
> Well it's fixed now, I found some code to put into the blank freecom.h file but this isn't what may have fixed it. I went back into windows and safely removed hardware and then shut down instead of restarted and it was right there on the desktop when I booted into Ubuntu. Oh well, the joys of a new OS.

Well, that would have been the obvious way to go first up but was under the impression you'd tried that. Even though USB is supposed to be 'hotplug', you always need to shut down the drive in windoze (or unmount device in Ubuntu). Not sure that shutting down or restarting windoze would have anything to do with it, as long as you have 'safely removed hardware' and unplugged the external drive. Not doing a clean windoze shutdown (either restarting or shutdown) can cause problems, but wouldn't of thought that one. You can restart from Ubuntu into Windoze or vice versa with no problem but anyways, it's working now so all good.

Have you tried taking the data out of the freecom.h file (or deleting it) and seeing if everything still works okay? You don't want to create another prob down the track with the rogue data in this file.

ps: an idea to switch the external drive on *after* you boot into an OS. My windoze box gets quite confused and all sorts of oddities if I boot with the external drive switched on. :) In ubuntu, right click, 'unmount volume'.

---

### Post by aeronotix on 2008-11-20
Well the problem seems to be back.

It's really getting annoying now. It was working fine, I could write/read with no problems (in fact it was working better than in Windows because I could access folders that windows wouldn't for some reason.) then I was off to work and didn't want to leave the hard drive on all day with nothing do, so I Right-Click, Unmount and wait then turn the hard drive off.

I come home and Ubuntu is still there waiting for me, I switch on the hard drive, lights flicker but seemingly no-one is home. All the commands I showed before are back to how they were before when it wasn't working (lsusb showing not much, fdisk -l showing only the hard drive I was booting off and a helluva lot of stuff with the dmesg that I couldn't see anything for the external hard drive.) 

To be fair, this is the only gripe I am having so far with Ubuntu. I love the ease, the speed (mine runs ridiculously good vs. Windows Vista) but this, this is what's stopping me going whole hog and delving right into this Linux business.

> **Bucky Ball said:**
> Well, that would have been the obvious way to go first up but was under the impression you'd tried that. Maybe but I'm pretty new to this OS.

---

### Post by razy60 on 2008-11-20
I had a similar problem with an external drive.
 The option i eventually took was to copy all the files that i could, onto another device, then completely reformatted the drive as a ntfs drive(i did it in that other os using swiss knife), works just fine now.
 That was the only way i could think of at the time.
If your external drive is powered by a mains plug always power it on before plugging it into your pc as it needs to be running so that your pc can see it, unmount, then power it off before switching your pc off or suspending it. At least thats what i found to work best.

Raz

---

### Post by aeronotix on 2008-11-20
> **razy60 said:**
> 
 The option i eventually took was to copy all the files that i could, onto another device, then completely reformatted the drive as a ntfs drive

I can't. The only other drive I have has 3.1GB left, this hard drive has my life on it.

I'm starting to give up.

---

### Post by psusi on 2008-11-20
When you unplug the usb connector, wait a few seconds, then plug it back in, do any new lines get added to dmesg?

---

### Post by razy60 on 2008-11-21
aeronotix wrote> I can't. The only other drive I have has 3.1GB left, this hard drive has my life on it.
If the files are that important then if it were me i would get myself another storage device, and copy the files. as i have been told on more than one occasion."backup your backups".
You sound as though you have a lot of data stored anyway so your going to need a new drive soon, may as well be now rather than later, that way you can try and get the flaky drive to work and not risk loosing the saved data.
It might not be ideal but it is the most practical.

Raz

---

### Post by Bucky Ball on 2008-11-21
> **razy60 said:**
> 
  i have been told on more than one occasion."backup your backups".


Something I was taught early on about backing up valuable data is the 'Grandfather/Father/Son' rule. One on the computer, one in another room and one in a different suburb in case the place burns down or anything drastic.

---

### Post by oaxacamatt1 on 2008-11-21
Hey aeronotix,
I had a similar problem to yours a little while ago.  I was trying to mount some insteral and external HD on my machine with 8.10.  I looked around the message groups and found someone that mentioned the prog. 'pysdm', it stands for Py Storage Device Manager.  It is really awesome.  Just install it using:

sudo apt-get install pysdm

Then when that is finished use:

gksu pysdm

Cheers,
Matt

---

### Post by aeronotix on 2008-11-23
psydm doesn't pick it up either, is it meant to show up straight away on the list on the left?

---

### Post by Bucky Ball on 2008-11-23
I played around with it and yes, my external drive shows up straight away in the left column. I know this sounds obvious, but have you tried a different usb cable?

---

### Post by aeronotix on 2008-11-23
I thought that since it was working in Windows the cable was fine.

I had an idea though, if I link it to my windows box there should be someway to access the drive over the network, right?

---

### Post by Bucky Ball on 2008-11-23
That could be possible, although a workaround rather than fix which is unfortunate. Make sure the external partitions are set to 'share' and show up that way in Windoze.

---

### Post by aeronotix on 2008-11-24
Yeah ok I think that's how I will overcome this then, thanks for all your help ESP. Bucky Ball! I won't mark this as solved because it isnt. Once again thanks!

---

### Post by iminhell on 2008-11-25
Through searching I eventually came across this thread.

For the novice like myself this is what worked for me (for how long is a mystery)

Go to "applications" -> add/remove programs -> in the search window type "pysdm" (just as matt mentioned) it will come up as a program called Storage Device Manager, add that and wait for it to download and install (pretty quick little file).
Once it is installed you can find it under System -> administration (I lost it after I closed the installer)
Select it and you will have a few drive's listed under the left side menu. This is where you select the drive you wish to mount/unmount. If you don't know what is what then run the 'sudo fdisk -l' command, that will give you the label of the external hard drive volume. Pick the appropriate one and then select 'assistant' and select 'allow any user to mount drive' (assuming it's not a network drive).


That is what fixed my troubles. Hopefully it helps others.

---

### Post by aeronotix on 2008-11-29
Well, for seemingly no reason at all; I have access to the drive. Let's see how long it lasts, hurrah!

---

