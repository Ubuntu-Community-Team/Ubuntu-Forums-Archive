---
title: "Can't see other hard drives"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by WheelDawg on 2006-11-17
Ok, I've looked around and seen a lot of info on mounting and stuff, but everyone seems to be having a slightly different issue than me.

As this is my first post here (already lurked and got around 15 questions answered from other topics w00t), let me explain my setup.

My computer has 3 physical hard drives:
C: = Main drive, has XP installed and the progs I use with XP
D: = partition of C that I use just for picture/image files
E: = drive I have Ubuntu 6.10 installed on.
F: = Music/video archives

So my problem is this. I want to be able to access my other drives. I can get to everything within my Ubuntu drive perfectly, but C, D, and F aren't showing up at all.

I consider myself to be of above average computer intelligence, unfortunately until yesterday all my experience is with Windows- so I'm not afraid of getting my hands dirty with the terminal, I just need to know what I'm doing, lol. 
I finally took the plunge and decided to try out Linux yesterday on an empty drive. This seems to be the only hurdle I have yet to smooth out in getting everything I need working in this OS.

Thanks in advance.

---

### Post by s_h_a_d_o_w_s on 2006-11-17
You should be able to acces your other hard drive with System -> ADministration -> Disks . In it you'll have to give it an acces path. I think a porgram aclled gparted will help you with partitions but i'm not sure about that one :-)

---

### Post by WheelDawg on 2006-11-17
> **s_h_a_d_o_w_s said:**
> You should be able to acces your other hard drive with System -> ADministration -> Disks . In it you'll have to give it an acces path. I think a porgram aclled gparted will help you with partitions but i'm not sure about that one :-)

There is no "Disks" under Administration.

There is, however, a "Device Manager" (hmm starting to sound like XP again lol) and in that list I can see all my dives mentioned, but I don't know how to use that info to access them.

---

### Post by taurus on 2006-11-17
Here you go...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by WheelDawg on 2006-11-17
I get this
> mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Argh what am I doing wrong... This is what I got from fdisk
> Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8354    67103473+   7  HPFS/NTFS
/dev/hda2            8355        9963    12924292+   f  W95 Ext'd (LBA)
/dev/hda5            8355        9963    12923904    7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7288    58540828+  83  Linux
/dev/hdb2            7289        7476     1510110    5  Extended
/dev/hdb5            7289        7476     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/hdc5               2       14593   117210208+   7  HPFS/NTFS

I'm mainly trying to get to my music, which is on the 120GB drive. It lists as /dev/hdc.

Here's my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c5e671ad-06ec-424f-b932-59358c606bdd /               ext3    defaults,erro$
# /dev/hdb5
UUID=fda853aa-9fec-49a6-811a-4b520561a513 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc        /windows        ntfs    nls=utf8,umask=0222 0  0

Any clues?

---

### Post by taurus on 2006-11-17
Oops.  The last line in your /etc/fstab should have been

```
/dev/hdc5 /windows ntfs nls=utf8,umask=0222 0 0
```

---

### Post by greeklegend on 2006-11-17
isnt /dev/hdc the music drive?
and you can mount your C and D drives by adding to your fstab...
```

/dev/hda1 /media/c ntfs users,ro 0 0
/dev/hda5 /media/d ntfs users,ro 0 0

```
just make sure you create /media/c and /media/d first ;)

---

### Post by WheelDawg on 2006-11-17
I'm such a n00b... lol

I found the problem. I was still thinking in Windows mode, waiting for the drive to appear in the "Places -> Computer" window, when it was under /windows the whole time.

Thanks guys, this really helped me out.

Some ppl may see these as annoyances to switching to Linux, but I kinda like getting my hands dirty with it, so to speak. It feels more personal that way.

---

