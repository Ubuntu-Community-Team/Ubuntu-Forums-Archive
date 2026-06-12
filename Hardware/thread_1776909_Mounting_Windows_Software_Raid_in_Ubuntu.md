---
title: "Mounting Windows Software Raid in Ubuntu"
date: 2011-06-06
forum: Hardware
---

### Post by rchille on 2011-06-06
Hello all

I have a computer that I'm dual booting between Ubuntu 11.04 and Win7 (Enterprise?)

I have a SDD that I've split up for the OSs, and a pair of HDD that I'd like to RAID0 together. I've read in a few places that Linux should be able to handle Win7's Software RAID and found this helpful post: [http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk]("http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk")

I ran through the instructions but got stuck in trying to mount the drives.

What I did:
1. Load Win7

2. Set both drives to GPT

3. Build the RAID0

4. Format to NTFS

5. Verify it works (copied some file to it)

6. Boot Ubuntu

7. Run: cat /proc/partitions
```
major minor  #blocks  name

   8        0  312571224 sda
   8        1       1024 sda1
   8        2     130048 sda2
   8        3  312440118 sda3
   8       32  312571224 sdc
   8       33       1024 sdc1
   8       34     130048 sdc2
   8       35  312440118 sdc3
   8       16   78150744 sdb
   8       17     102400 sdb1
   8       18   38972416 sdb2
   8       19          1 sdb3
   8       21   39072768 sdb5
   8       48  156290904 sdd
   8       49  156288000 sdd1
   9        0  624880128 md0

```

8. Run: sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sd[c|a][1-3] /dev/sd[a|c][1-3]
```
mdadm: array /dev/md0 built and started
```

9. Run: sudo mount -t ntfs-3g /dev/md0 /media/raid0
```
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I've swapped the devices around in all possible combos (8) and I get the same results each time.

Poking around via Google a bit more, I see that other have this working, so I'm hoping there's just something silly I'm missing.

Any suggestions?

Thanks!

---

### Post by rchille on 2011-06-06
So 'bout half way through posting that, I thought "Why not try MBR instead of GPT"?

I started over, used MBR on the disk and received a very different partition list:
```
   8       32  312571224 sdc
   8       33  312568832 sdc1
   8        0  312571224 sda
   8        1  312568832 sda1
   8       16   78150744 sdb
   8       17     102400 sdb1
   8       18   38972416 sdb2
   8       19          1 sdb3
   8       21   39072768 sdb5
   8       48  156290904 sdd
   8       49  156288000 sdd1
   9        0  625137664 md0

```

The right combo (for me) after that was:
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda1 /dev/sdc1

So it seems that Linux CAN handle GPT, and it can handle MS's Dynamic Disk (which Win uses for RAID), it just can't do both at once (at the moment!).

I'm currently mounting and creating files on both Ubuntu 11.04 and Win 7 and can access them on either OS! :popcorn:

I hope this helps someone out there.:D

---

### Post by ronparent on 2011-06-08
The Win7 'software raid' uses a MB based chip set to set up the raid. To access it within Ubuntu you would use dmraid not mdadm to access it. In my experience dmraid is not installed with the Ubuntu installation unless the Ubuntu itself is installed to the raid. To access the NTFS formatted raid partitions simply install dmraid (sudo apt-get install dmraid). On completion of this the NTFS raid partitions should be automatically found and be mountable within nautilus.

Conversely if you use mdadm to set up a software raid that raid would not be usable to windows.

Post if you need more.

---

### Post by rchille on 2011-07-11
Sorry for the late follow-up (cleaning out a months worth of email back-log)

Just want to make sure that we are using the same terminology:

Software RAID: 
RAID Systems with no dedicated hardware

Fake RAID: 
RAID with a controller (usually on the motherboard) but offloading the hard work to the CPU (usually needs drives of some type)

Hardware RAID: 
Usually with a dedicated card, transparent to OS, All work is done on dedicated hardware

I'm not sure how Win 7 handles Fake VS Software RAID, in Linux mdadm seems to be best for software RAID while dmraid seems to be the choice for Fake Raid (Unsure if you can switch these).

My issue was that my motherboard didn't have an on-board RAID controller (So Fake RAID was out) nor did have expansion slots for a Hardware RAID card. 

I used the Win 7 Disk Manager to build a Software RAID and then on the Ubuntu side, used mdadm to tell the OS how Win 7 configured the Software RAID it had setup. 

The magic is that both Win 7's RAID system and mdadm deal have the same configuration so there is interoperability between the two. The end result is a RAID that either OS can read and write to depending on which I've booted into. 

Which is quite cool. :)

---

### Post by stolpee on 2012-02-24
Thanks for the heads up!

I'm a little stuck though...
 
I have 3 arrays, 1 Dynamic MBR and 2 Dynamic GPT. Full of data, so I don't wanna delete de partitions to remake into MBR (which works like a charm though) Is there NO WAY of getting the Dynamic GPT arrays to work? I guess conversion is out of the question? : P

---

### Post by CalcProgrammer1 on 2012-05-09
I'm facing the same issue as described earlier in this post.  I was planning on reformatting my RAID, but if it's possible to mount my existing setup in Linux I might stick with it.

My current setup is a Windows Server 2003 dynamic disk RAID-5 array (3x 1.5TB Samsung HDD on ordinary SATA controller).  I'm not using fakeraid, this is purely software.  The array is formatted NTFS.

I plan on migrating the machine (which is a home fileserver for media and data) to Ubuntu 12.04 as my current hardware is aging and uncooperative when it comes to booting (Server 2003 will not boot from the SATA-mode controller and the IDE-mode SATA controller causes system crashes, so I've been booting it off a flash drive with GRUB4DOS and it doesn't like flash drives either).  I plan on buying new hardware soon enough, but will set up the new RAID on the current hardware first.

I was playing around with mdadm today on a VM and got a 3 drive RAID-5 set up and formatted ext4.

I'm assuming (based on a previous post in this thread) that I need to do something like

sudo mdadm --build /dev/md0 --chunk=64 --level=5 --raid-devices=3 /dev/sd[bcd]

to get the array functional again?  The server has one smaller drive for its boot disk, so I'm not booting off the RAID.  I'm assuming this will be sda.  The other three should be sdb, sdc, sdd.

---

### Post by rchille on 2012-05-09
In my case, success or failure was all based on how I'd set the RAID up in Windows and I'm not sure how Win Server 2003 does it vs Win7.

I would start with running a:
```
cat /proc/partitions
```
and see what your partitions look like.

I have a feeling that you'll be running something like: 
```
sudo mdadm --build /dev/md0 --chunk=64 --level=5 --raid-devices=3 /dev/sdX1 /dev/sdY1 /dev/sdZ1
```

Back when I was looking at this 9 months ago, I remember that for certain way the Win configured RAIDs that mdadm wouldn't not be able to init level 5 correctly. That might have changed, or not apply to Win Server 2003, but it is a consideration.

---

