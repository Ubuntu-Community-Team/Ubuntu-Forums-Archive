---
title: "Help with HD mounting"
date: 2004-10-21
forum: Hardware &amp; Laptops
---

### Post by BugsyMalone on 2004-10-21
I'm new to Linux and I've been trying to get my extra storage drive mounted. I went to Computer-&gt;Disks and the drive shows up there, but when I click on it I get this message. "Unable to mount the selected volume - - mount: dev/hdb already mounted or /mnt/hdb busy." This is the only place I could find to access the drive. If I've done something wrong, or there's another place to access the files on the drive please let me know.

I love Ubunta BTW...  :)

---

### Post by Vulc on 2004-10-21
do this

sudo mkdir /mnt/shared

sudo pico /etc/fstab

then add a line sort of like this

/dev/hdb#       /mnt/shared     vfat    ro,umask=000    0       0

then sudo mount /dev/hdb#

# is the parition number (was 5 in my case since my paritition was extended
should be good to go after that

---

### Post by FLeiXiuS on 2004-10-22
If its already in use, then why would you want to mount it again?

**BugsyMalone**
I recommend to do this..

First, find which drives are mounted and where they are mounted to.
```
df -h
```

Second, If the drive is not mounted, then your going to need to know the hd letter and the hd number, IE hd_a_ - hda_0_ 

To determine these, 
```
fdisk -l
```

Once you've gather all of your info, then its time to procede into some of what  _Vulc_ was talking about.  He wasn't too explanatory.  So allow me to be brief.

/etc/fstab is the file that will auto-mount partitions to linux distrobutions.

To edit this file, open it as root.  Start a terminal then type:
```
sudo gedit /etc/fstab
```

At the end of the file, create a few spaces and type the following information. 
(You will need to correct some of it in order to fit your system.)

```

#Manual Mounted Drives
/dev/hd# /mount/path fs ro,auto,uid=0000,gid=0000,umask=0000 0 0

```

Replace 'hd#' with your correct letter and number as mentioned above.

Replace '/mount/path' to the path where you would want to mount this to.  Usually you can create a folder called whatever in your home directory (as standard user) and mount it there.  "IE: /home/fleixius/drives/hda1" 

Then replace 'fs' with the file system of the partition your mounting. 

File Systems 
vfat (fat32)
ntfs
reiserfs
ext2
ext3
...etc..etc..etc...

Once your done that, you will need permissions to access this newly mounted partition.  Replace uid=0000 with uid=userIDnumber and gid=0000 with gid=groupIDnumber.  If there is only 1 user on the system by default the uid=1000 and the gid=1000.  So replace them respectively.  

If this is not the first account created...
```

sudo gedit /etc/passwd
sudo gedit /etc/groups

```

You will find them there...Once your finished editing the /etc/fstab SAVE immediately and then type
```

mount -a

```
This will remount all of the partitions located in /etc/fstab.

I hope this has helped.. if you want to check your mount status type:
```

df -h

```

I hope I have clearly explained all of the above to you, this is basics of mounting.  Enjoy Ubuntu its fantastic and welcome to Ubuntu Forums!  See Yah Around! :P

---

### Post by BugsyMalone on 2004-10-23
FLeiXiuS, thanks for the advice. I don't think I worded my previous post correctly. I wasn't trying to mount the drive again, I was just trying to access the data on the drive. I clicked the "Disks" section because that was the only place I could see the drive. Anyway,,, 

I still can't get to the files on the drive I need, although I did manage to get my windows drive mounted. Here's what I did:

I ran the "df -h" command and only the Linux drive was mounted.

I knew the drive in question had only one partition and it was named hdf. I created a folder in the /home/kelly directory named "shared" then one within "shared" named "hdf."

I did "sudo gedit /etc/fstab" and with the alterations to the "/dev/hd# /mount/path fs ro,auto,uid=0000,gid=0000,umask=0000 0 0" 

I'm the only user, so I entered "/dev/hdf /home/kelly/shared/hdf vfat ro,auto,uid=1000,gid=1000,umask=0000 0 0"

I saved the file then went back into terminal and entered "sudo mount -a."  I got this message: mount: /dev/hdf already mounted or /home/kelly/shared/hdf busy." It's the same one I got before.

I hadn't intended to mount my Windows drive, since I keep all the important files on the other drive, but I decided to do it to see if the same thing happened. I made a folder within the "shared" folder and named it "hda1."  I made an entry in the fstab file: "/dev/hda1 /home/kelly/shared/hda1 vfat ro,auto,uid=1000,gid=1000,umask=0000 0 0" and then ran the "mount -a" command. The drive mounted immediately and it's in the home directory. I'm really confused about what's happening with this drive. Any advice would be more than appreciated...

---

### Post by FLeiXiuS on 2004-10-23
The hdf drive needs a partition label.  

IE: hdf0

I would try editing the /etc/fstab and mount the /dev/hdf0 then reply with what happens.

---

### Post by BugsyMalone on 2004-10-23
I changed the name in both the fstab and the destination folder to hdf0 and I got this message, "mount: special device /dev/hdf0 does not exist."

---

### Post by hoosfoos on 2004-10-23
Very nice directions FLeiXiuS!  You are the first guru who I've seen in a Linux forum who takes time to explain things thoroughly instead of some cryptic, curt response.
Thanks.

---

### Post by BugsyMalone on 2004-10-25
Okay, I'm still trying to get this drive mounted. After doing some re-arranging, re-installing and deleting, here's my HD set up at the moment:

hda-28 gig vfat in two partitions with XP and Ubunta in a duel boot.

hdb-75 gig vfat in one partition with the most important files copied from the hdf drive.

hdf-150 gig vfat, a paperweight according to Ubunta.

I don't need nor want my Winblows partition mounted.  The only reason I'm keeping it around is my printer is not supported by Linux and I need to print occasionally. I can just go temporarily into Windows to print a document. Cheaper than buying a new printer...

I tried to mount the hdb drive, and a created a directory /home/kelly/shared/hdb1, and made an entry in fstab "/dev/hdb1 /home/kelly/hdb1 vfat ro,auto,uid=1000,gid=1000,umask=0000 0 0."

Did the "mount -a" command and bingo, the drive mounted right up, except...it's read only. I need to be able to write to that drive. I'm involved in a writing project and all my Word files are there. What can I change to be able to write to this drive?

The 150 gig is connected via a Promise IDE card, could this be why I'm not getting it mounted?

I have to admit I'm beyond frustrated about this. I really want to ditch Windows, and I've tried several distros, all with major glitches. This one has worked the best, but I'm not going to give up a 150 gig hard drive to use it.

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=hoosfoos]Very nice directions FLeiXiuS!  You are the first guru who I've seen in a Linux forum who takes time to explain things thoroughly instead of some cryptic, curt response.
Thanks.[/QUOTE]

Thank you very much for your compliments!  I try my hardest to explain clearly.

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=BugsyMalone]I changed the name in both the fstab and the destination folder to hdf0 and I got this message, "mount: special device /dev/hdf0 does not exist."[/QUOTE]


To get the hard drives mount ID...

```
fdisk -l
```

---

### Post by BugsyMalone on 2004-10-25
Here's what I get with that command:

####@ubuntu:~ $ fdisk -l
Cannot open /dev/hdf
Cannot open /dev/hda
Cannot open /dev/hdb

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=BugsyMalone]Here's what I get with that command:

####@ubuntu:~ $ fdisk -l
Cannot open /dev/hdf
Cannot open /dev/hda
Cannot open /dev/hdb[/QUOTE]


Sorry, you must be ran as root!  As you should with the other mount commands!

```
sudo fdisk -l
```

---

### Post by BugsyMalone on 2004-10-26
I'll learn when to and not to run as sudo one of these years. LOL Anyway, nervous breakdown averted. I ran it with the sudo command and the drive is dhf2. Amended everything, and the drive mounted right away. I then realized I had it set to "ro" instead of "rw." Changed that and I can write to the disk. Thank you, thank you, thank you FLeiXiuS.

---

### Post by nyx on 2004-10-26
[QUOTE=BugsyMalone]I'll learn when to and not to run as sudo one of these years. LOL Anyway, nervous breakdown averted. I ran it with the sudo command and the drive is dhf2. Amended everything, and the drive mounted right away. I then realized I had it set to "ro" instead of "rw." Changed that and I can write to the disk. Thank you, thank you, thank you FLeiXiuS.[/QUOTE]
 FLeiXiuS,
I'm running into this problem (see the end where I put in "sudo gedit  /etc/fstab")
> 
root@pandora:~ # fdisk -l

Disk /dev/hda: 40.0 GB, 40060403712 bytes
16 heads, 63 sectors/track, 77622 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       76629    38620984+  83  Linux
/dev/hda2           76630       77622      500472    f  W95 Ext'd (LBA)
/dev/hda5           76630       77622      500440+  82  Linux swap

Disk /dev/hdb: 120.0 GB, 120000000000 bytes
16 heads, 63 sectors/track, 232514 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9688     4882720+  82  Linux swap
/dev/hdb2            9689       77505    34179768   83  Linux
/dev/hdb3           77506      145322    34179768   83  Linux
/dev/hdb4          145323      232514    43944768   83  Linux
root@pandora:~ # sudo gedit /etc/fstab

(gedit:6102): Gtk-WARNING **: cannot open display:

Okay I fixed the gtk warning by not doing it in root. 
Now my problem is 
> 
root@pandora:~ # mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       or too many mounted file systems

How do I tell what I formatted it as?  I could have sworn I did it ext3
and I've only got one user, and it said its 1000 and 1000 so I'm not sure why that'd be wrong. 

What does superblock mean??

Like what was said above, thanks majorly for explaining all of this, I didn't know what command showed everything, so thanks for mentioning fdisk -l !!!

---

### Post by nyx on 2004-10-26
Got it working
had to replace uid=0000,gid=0000  with user
and delete umask=0000

---

### Post by Xanthous on 2005-06-29
This is a nice presentation with clear instructions, thank you.  Yet, i seam to be missing something.
After following the instructions, I get this error:

```
root@ubuntu:/home/dna # mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

My fstab is as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none        swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/dv       ntfs    umask=0222      0       0
/dev/hda6       /media/ang      ntfs    umask=0222      0       0

/dev/hdc1       /media/drive ext3 ro,auto,uid=81,gid=1000,umask=0000 0 0

```


Some more info:

```
root@ubuntu:/home/dna # cat /proc/partitions
major minor  #blocks  name

   3     0   78150744 hda
   3     1   15992676 hda1
   3     2          1 hda2
   3     5   30844768 hda5
   3     6   30595761 hda6
   3     7     714829 hda7
  22     0   80418240 hdc
  22     1   80413326 hdc1
 254     0   15992676 dm-0
 254     1   30844768 dm-1
 254     2   30595761 dm-2
 254     3     714829 dm-3
 254     4   80413326 dm-4
root@ubuntu:/home/dna # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              16G  7.1G  7.2G  50% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hda5              30G   24G  6.3G  79% /media/dv
/dev/hda6              30G   27G  2.3G  93% /media/ang
/dev                   16G  7.1G  7.2G  50% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
root@ubuntu:/home/dna # fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1991    15992676   83  Linux
/dev/hda2            1992        9729    62155485    f  W95 Ext'd (LBA)
/dev/hda5            2081        5920    30844768+   7  HPFS/NTFS
/dev/hda6            5921        9729    30595761    7  HPFS/NTFS
/dev/hda7            1992        2080      714829+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       10011    80413326   83  Linux

```

How do I clean up this mess?  I had data on the 2 ntfs drives, which once copied over to a linux drive, I will format to linux also.  

Thank you all!  Ubuntu is really the way to go!

---

