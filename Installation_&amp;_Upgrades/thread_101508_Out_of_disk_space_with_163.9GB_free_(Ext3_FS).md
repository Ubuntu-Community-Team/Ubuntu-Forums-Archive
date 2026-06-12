---
title: "Out of disk space with 163.9GB free??? (Ext3 FS)"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by MistaED on 2005-12-09
Hello, I have had a reoccurring problem with two machines. The first one has a partition of about 60gb, formatted with ext3 with largefile4 and the 5% super user setting. It always got up to about 15 or 20gb and said "you are out of disk space" when there is obviously space free. I thought this was just a freak occurance, but I formatted the same partition into FAT32 and all is fine.

Now with my main box, I recently formatted my 200gb from NTFS to Ext3 because I found out about this driver [http://www.fs-driver.org/](http://www.fs-driver.org/) But just today I was copying files to it, and it got up to 10% disk usage and said "you are out of disk space". WTF? I don't understand this at all.

With other PC's, and my external hard drive, they haven't struck this problem, so I just wonder why this is happening. By the way, this 200gb is formatted with the largefile4 option and 1% reserved for the super-user. I have not used this drive at all under windows yet so it can't be the Win2000/XP Ext2 fs-driver.

Thank you
-MistaED

---

### Post by cpminga on 2005-12-11
Any thoughts on this? I ran into this problem this morning. I tried deleting some unnecessary files when I started getting these disk space error messages. I think i've deleted nearly two gigs of stuff but i still can't log back in because GDM is still complaining about disk space. I had to boot up to a live cd and when i mount my HD it's still saying that there's 100%  usage on my Ubuntu partition. Any thoughts on how i can reclaim some space so i can boot back into Ubuntu?

---

### Post by taurus on 2005-12-11
From your LiveCD, what does this command reports about your HD,

df -h

Also, how did you partition your harddrive anyway?  Did you have the entire space as / or did you break it up to other partitions?

---

### Post by cpminga on 2005-12-11
[QUOTE=taurus]From your LiveCD, what does this command reports about your HD,

df -h
[/QUOTE]

Filesystem            Size  Used Avail Use% Mounted on
/dev/root             165M  6.0M  159M   4% /
/dev/sde2             5.5G  129M  5.1G   3% /mnt/sde2
/dev/sde3              49G   46G     0 100% /mnt/sde3

[QUOTE=taurus]
Also, how did you partition your harddrive anyway?  Did you have the entire space as / or did you break it up to other partitions?[/QUOTE]
Well i'm not sure if this is what you mean but I have a WinXP partition using about half of 40gigs (NTFS) then i have a swap (ext2 i think) around 150MB and then my Ubuntu which is ext3 of course which is around 45 gigs as you can see. I also have about five gigs which i just converted from fat32 to ext3 in case i had to use that for something while i fix this problem

---

### Post by taurus on 2005-12-11
Can I see your /etc/fstab as well?  Your "hf -h" looks a little odd especially the second line, /dev/root!!!  :confused: 

more /etc/fstab

p.s.  Just so you know, there is no filesystem for swap so it's not ext2...  It's sw!

---

### Post by cpminga on 2005-12-11
[QUOTE=taurus]Can I see your /etc/fstab as well? Your "hf -h" looks a little odd especially the second line, /dev/root!!! :confused: more /etc/fstab[/QUOTE] [QUOTE=taurus]p.s. Just so you know, there is no filesystem for swap so it's not ext2... It's sw![/QUOTE] Shows you what i know! ;) I should have mentioned that my live cd is PCLinuxOS. When i freak out i just grab the first thing i can find which was that so i don't know if that is messing things up. ```
# This file is edited by fstab-sync - see 'man fstab-sync' for details

### Entries below this line were automatically added by hwdetect v0.5.9-20050602
# ROOT
/dev/root	/	rootfs	defaults	0 0
# USB
none	/proc/bus/usb	usbfs	defaults	0 0
# PROC
none	/proc		proc		defaults	0 0
# PTS
none	/dev/pts	devpts	mode=0620	0 0

# fd: H1440
/dev/fd0	/mnt/floppy	auto	user,exec,rw,noauto,iocharset=iso8859-1,codepage=850,umask=0	0 0

# cdrom: TSSTcorpCD/DVDW TS-H552B
/dev/hda	/mnt/cdrom	auto	user,exec,ro,noauto,iocharset=iso8859-1,codepage=850,umask=0	0 0

# cdrom: HL-DT-ST RW/DVD GCC-4481B
/dev/hdb	/mnt/cdrom2	auto	user,exec,ro,noauto,iocharset=iso8859-1,codepage=850,umask=0	0 0

# /dev/sde1, size=84052080, type=7: NTFS (primary)
/dev/sde1	/mnt/win_c	ntfs	user,exec,ro,noauto,iocharset=iso8859-1,umask=0	0 0

# /dev/sde2, size=11630997, type=11: FAT32 (primary)
/dev/sde2	/mnt/sde2	ext3	user,exec,rw,noauto	0 0

# /dev/sde3, size=102301920, type=131: Journalised FS: ext3 (primary)
/dev/sde3	/mnt/sde3	ext3	user,exec,rw,noauto	0 0

# /dev/sde5, size=3020157, type=130: Linux swap (extended)
/dev/sde5	swap	swap	defaults	0 0
```

---

### Post by taurus on 2005-12-11
Is that /etc/fstab from your Ubuntu???  How many harddrives do you have on your machine and are they SATA???  Looks to me like you have two CD-ROMs, /dev/hda & /dev/hdb, and a SATA harddrive, /dev/sda!  What is the output of this command then?

fdisk -l /dev/sda

---

### Post by cpminga on 2005-12-11
yeah, it's from Ubuntu. I have one harddrive and i just took the side off my PC to make sure it's a SATA; it is. I have two optical drives. Aside from that, i have a floppy and muti-media card reader.

"fdisk -l /dev/sda" returns no output.

---

### Post by cpminga on 2005-12-11
fdisk -l /dev/sde3

Disk /dev/sde3: 52.3 GB, 52378583040 bytes
255 heads, 63 sectors/track, 6368 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sde3 doesn't contain a valid partition table


I thought this looked interesting. Should my Ubuntu partition have a partition table?

---

### Post by taurus on 2005-12-11
Okay, even though GDM can't start, running out of space, you can still get into a terminal right!  Wait for the system to boot (without the LiveCD) and hold down <Ctrl><Alt>F2.  Log in and see what does it say,

sudo fdisk -l /dev/sda
-or-
sudo fdisk -l (I am sure it will complain about it, telling you that you need to specify a disk to "display"...)

---

### Post by cpminga on 2005-12-11
fdisk -l

```

disk /dev/sda" 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/tracks, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

device Boots     Start        End       Blocks             Id     System
/dev/sda1 *      725        5956     420226040     7     hpfs/ntfs
/dev/sda2         1            724        5815498+       b     W95 FAT32
/dev/sda3         12902    19269    51150960      83   Linux    
/dev/sda4          79270   19457    1510110         5    Extended
/dev/sda5          19270   19457     1510078+     82   Linux swap / solaris

Partition table entries are not in disk order

```

---

### Post by taurus on 2005-12-11
[QUOTE=cpminga]fdisk -l

```

disk /dev/sda" 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/tracks, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

device Boots     Start        End       Blocks             Id     System
/dev/sda1 *      725        5956     420226040     7     hpfs/ntfs
/dev/sda2         1            724        5815498+       b     W95 FAT32
/dev/sda3         12902    19269    51150960      83   Linux    
/dev/sda4          79270   19457    1510110         5    Extended
/dev/sda5          19270   19457     1510078+     82   Linux swap / solaris

Partition table entries are not in disk order

```[/QUOTE]
That is the weirdest looking partition table that I've ever seen!!!  Your second partition starts at the begining of the disk while your first partition starts after that.  Then, your third partition doesn't even start at the end of the first partition...  What program did you use to partition your harddrive anyway???

Here is what my partition looks like...

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         203      102280+  83  Linux
/dev/hdb2             204        2285     1049328   82  Linux swap / Solaris
/dev/hdb3            2286      144509    71680896   83  Linux
/dev/hdb4          144510      238216    47228328   83  Linux

---

### Post by cpminga on 2005-12-11
i just used whatever Ubuntu provides in its intaller. Since then i've only done a couple of tweaks (resize, reformat) with gparted which shouldn't have done anything too major, i suppose.

---

### Post by cpminga on 2005-12-11
When i'm in the CLI and try to startx, i get a message 

"server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock
and start again"

do you think that may have something to do with it?

---

### Post by taurus on 2005-12-11
I have no idea what you did and don't know much about gparted since have never used it before but I think you should seriously consider re-partition your drive over again...

---

### Post by jmcelroy on 2005-12-11
Could you be running out of i-nodes? Do a 'sudo tune2fs -l /dev/sda3' and see what the line 'free inodes' says?

---

### Post by cpminga on 2005-12-11
[QUOTE=jmcelroy]Could you be running out of i-nodes? Do a 'sudo tune2fs -l /dev/sda3' and see what the line 'free inodes' says?[/QUOTE]

free inodes: 6063283

---

### Post by jmcelroy on 2005-12-11
not out of inodes then :)

---

### Post by MistaED on 2005-12-11
I think in my case I ran out of inodes =E Hence having 40k of files/folders using the largefile4 option. I didn't know, but at least now I've backed up everything and have used the default settings.

Btw, is there any painless ways of adding more inodes instead of formatting it again?

-MistaED

---

### Post by cpminga on 2005-12-11
I got it! I want to thank all of you, especially taurus, for your time, patience and help. It turned out that the backups that Ubuntu makes was taking up about 30 gigs of space. I deleted most of those from /var/archives and all was back to normal! Thanks again! This is by far the best community for any product or service i've come across!

---

### Post by kingsidy on 2005-12-11
Sometimes when you delete stuff, it is still in the trash. When you are a regular user and u delete files owned by root, emptying the trash does not remove them at all. One sugestion is to forcefully empty trash. at the terminal type in: > sudo rm -fr $HOME/.Trash/ it should free space from trash

---

### Post by taurus on 2005-12-11
Oh yes, the good old /var/archives.  It's always a good idea to clean that out every now and then since everytime you install something with apt-get/synaptic, a copy of that program is taking up space in /var/archives... 

And you're welcome.  :cool:

---

