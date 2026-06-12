---
title: "unable to access internal HDD"
date: 2014-07-16
forum: Hardware
---

### Post by vap1485 on 2014-07-16
Greetings. I'm having trouble mounting my HDD

when I click it to load it I get the following

Error mounting /dev/sdc at /media/djehuti/6d5b411c-4dfe-4c69-81e3-fb32a0749fc5: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc" "/media/djehuti/6d5b411c-4dfe-4c69-81e3-fb32a0749fc5"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Bashing-om on 2014-07-16
vap1485; Hi !

I will start this ball rolling.
What does 'fdisk' report about the drive ?
```

sudo fdisk -lu

```
And what is the SMART results from running  a full test on the drive from the "disk" utility ?

If those results are positive, will look at mounting that drive from terminal, see what then results.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-07-16
You can get the filesystem type for your partitions with this command, lower case Letter L in the command.

```
sudo parted -l
```

---

### Post by vap1485 on 2014-07-16
Okay. So it's a 3tb HDD and theres many videos in it. 
 

sudo fdisk -lu 
Brings the following

```


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2047  4294969341  2147483647+   f  W95 Ext'd (LBA)
Partition 1 does not start on physical sector boundary.
/dev/sdc5            2048  4294969342  2147483647+  83  Linux
```

Before it was 1 partition now after a few things I've tried, its like this :/ I tried a few things like running testdisk to recover the partition and running the gparted error scanner. Also I used gpart in the terminal to recover it. All has left it in this state. I'm sure if I use photorec, that I can recover the videos, but the folder structrue will be in disarray along with the file names (if I'm not mistaken) 

so! now I'm trying to fix it. I'm running the gparted scanner now, so my computer is going much slower. 


sudo parted -l
brings 

```
Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2047  4294969341  2147483647+   f  W95 Ext'd (LBA)
Partition 1 does not start on physical sector boundary.
/dev/sdc5            2048  4294969342  2147483647+  83  Linux


```

...guess those are the same command

---

### Post by yancek on 2014-07-16
Interesting.  Your output with parted command is very different from what I get.  See below:

```
~$ sudo parted -l
Model: ATA ST3320418AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      107MB   42.5GB  42.4GB  primary   ntfs
 4      42.5GB  307GB   265GB   extended
 5      42.5GB  63.1GB  20.6GB  logical   ext4

```  

The parted output gives the filesystem type rather than just 'linux'.  Anyhow, looking back at your original post with the output from your last post sdc1 is an Extended partition so there is not data on it.  You have sdc5 in that Extended partition with a Linux filesystem of some type.  In your first post, the command you posted was mounting the drive rather than the filesystem on the partition, should have been mount /dev/sdc1.  Since that is an Extended partition, try mounting sdc5 which is probably where your data is .

Have you gone to your /media/djehuti/ directory to see if 6d5b411c-4dfe-4c69-81e3-fb32a0749fc5 shows as that is where partitions on external usually are in Ubuntu.

---

### Post by vap1485 on 2014-07-17
In media/djehuti/ it 6d5b411c..... is there but it's empty. When I try to open it in Gparted, it shows the hard drive as grey and 'unallocated'

---

### Post by Bashing-om on 2014-07-17
vap1485; Shheesshh....
I see:
> 
/dev/sdc1            2047  4294969341  2147483647+   [color=red]f  W95 Ext'd (LBA)[/color]

A Windows extended partition. And within this Windows Filesystem is an attempt to have the linux file system (??) as sdc5 .
In addition you have no swap partition - with enough ram that is not a big factor but will not be able to hibernate ubuntu.
I can not see how a linux file system can possibly function from within a Window's File system.

I have no clue as to how this could have come about, and as I see it, the only remedy I can see is to redo the partitioning and (RE-)install the operating system(s).

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by vap1485 on 2014-07-17
This is not the HDD that I have the OS on. There's only videos in there.

---

### Post by yancek on 2014-07-17
I think your posted the output of fdisk twice in your earlier post.  Post the sudo parted -l output.
Have you been able to access this partition and the video files on them previously?  or did you just move them there?  Have you tried creating a mount point and manually mounting sdc5?  Do you know how to do that?

---

### Post by oldfred on 2014-07-17
If you have an extended partition, then you have MBR(msdos) partitioning. 
But if it is a 3TB drive you can only partition it with gpt if you want all 3TB.
MBR only goes to 2TiB since it was designed over 30 years ago and even TB was not heard of back then.

       [http://www.wolframalpha.com/input/?i=3TB+in+TiB](http://www.wolframalpha.com/input/?i=3TB+in+TiB)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by vap1485 on 2014-07-17
I was able to access the videos before. I've had this HDD for months now. I've been adding to and accessing the videos for some time now. I started using plex so the whole house can have access to them. Plex was unable to access them because of permission issues. Thats where the problem started. Its difficult to tell exactly what I did (because it was a lot) but suffice it to say I lost the data one time but was able to recover everything after some tinkering. All my stuff was in the lost+found folder. I restored everything to their proper folder and went back to using plex fine. categorizing all my videos and audio. after I restarted it was gone again and unable to access it. 


The HDD was ext4 before. I dont know why its MBR before. I had all the 3tb in use before. Is there a way to restore it to ext4 w/o erasing the HDD? Im sure the videos are still there, just the partition table is gone.


ANYWHOO I just used testdisk to restore the partition table. I had named it '3TB Internal' testdisk had that label in one of the partitions, so I chose that one and selected 'write' after that, it asked me to restart. when I did my whole computer would freeze at at the Motherboard screen. after sine troubleshooting, I found that it was the internal hdd stopping my CPU from starting. I disconnected the SATA cable from the MB and now it starts. So that's where I am now :/


_**EDIT: **_
Okay, so I have moved the internal 3tb HDD to a hotswap tray I have on the front of my computer. for some reason, my comp starts up now. and the OS recognizes it as '2.2 TB Volume. But all that shows is sdc1 which is where my stuff was. 


sudo parted -l 

Model: ATA TOSHIBA DT01ACA3 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2199GB  2199GB  primary



Also, trying to mount it gives me this:

Unable to access &#8220;2.2 TB Volume&#8221;

Error mounting /dev/sdc1 at /media/djehuti/6d5b411c-4dfe-4c69-81e3-fb32a0749fc5: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/djehuti/6d5b411c-4dfe-4c69-81e3-fb32a0749fc5"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


**so we're getting somewhere...**

---

### Post by yancek on 2014-07-17
How are you trying to mount the partition?  Are you doing it from a terminal or just clicking on it in the /media directory?

It's interesting that your parted output does not show the actual filesystem type.  When I run that command it shows the actual filesystem such as ntfs, ext4, ext3, reiserfs or whatever while yours just shows the type partition and not the filesystem type.  As explained above, sdc1 is an Extended partition.  That means it is a primary partition being used as a container for logical partitions, in your case just the one logical partition sdc5.  An extended partition does not contain data so trying to mount sdc1 is not going to get you anywhere.  There may be other problems but I would suggest you create a mount point for sdc5:  sudo mkdir /mnt/sdc5, after that try to mount it from a terminal:  sudo mount -t ext4 /dev/sdc5 /mnt/sdc5

Posting the output from that command if it fails should point us in the right direction.

---

### Post by vap1485 on 2014-07-17
I've since moved the HDD to a different slot. Before My computer wouldn't start with it in the same place. So now it's located @ /dev/sdh1

I did your commands in terminal but used sdh1 instead. here's the output:

[B]mount: wrong fs type, bad option, bad superblock on /dev/sdh1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

---

### Post by oldfred on 2014-07-17
When you used testdisk, did you choose gpt or MBR(msdos)?
 If a 3TB drive you had to choose gpt at the first screen.

---

### Post by vap1485 on 2014-07-17
> **oldfred said:**
> When you used testdisk, did you choose gpt or MBR(msdos)?
 If a 3TB drive you had to choose gpt at the first screen.

I chose the one at the top (intel.............)

---

### Post by oldfred on 2014-07-17
First is MBR, second is gpt.

---

### Post by vap1485 on 2014-07-17
I chose the first one

---

### Post by oldfred on 2014-07-17
But if a 3TB drive it has to be gpt to use all 3 TB, MBR has a max of 2.2TB or 2TiB.

Try again with the gpt choice, you may be able to recover gpt partition structure and then the entire thing. But if too many changes or other writes it may be too late.

---

### Post by vap1485 on 2014-07-17
Ahh! I wish I knew that. But now my computer wont start up at all while that HDD is connected. whether I use different SATA cables, or connect it to a hot swap bay, my computer just isn't having it.

-________-

---

### Post by oldfred on 2014-07-17
UEFI or BIOS has to read drive to enumerate it for system to use it and determine if a bootable device or a data drive.
If issues prevent that then you may not be able to recover it and if BIOS cannot see it, no system will be able to mount it or fix it.

Not sure what to suggest as you need to be able to boot with drive plugged in to be able to run recovery tools.

---

### Post by vap1485 on 2014-07-17
Depressing... well I guess I'll keep trying to get it back again. :/

---

### Post by yancek on 2014-07-17
> I did your commands in terminal but used sdh1 instead. here's the output:

I'm not sure why you keep trying to mount the first partition.  You have been told several times by more than one person here that it is an Extended partition and there is no data on it and the only data partition that showed on that drive is sdc5.  So if it is now sdh, you need to try to mount partition 5 not 1.  And your parted output wasn't complete for whatever reason as it did not show the actual filesystem type as it usually does so we don't know that it is ext4, it could be something else .

---

### Post by vap1485 on 2014-07-18
> **yancek said:**
> I'm not sure why you keep trying to mount the first partition.  You have been told several times by more than one person here that it is an Extended partition and there is no data on it and the only data partition that showed on that drive is sdc5.  So if it is now sdh, you need to try to mount partition 5 not 1.  And your parted output wasn't complete for whatever reason as it did not show the actual filesystem type as it usually does so we don't know that it is ext4, it could be something else .

Ah I guess I didn't understand that part. But now I can't even access the drive. When its in my PC the computer hangs at the motherboard splash screen.

---

### Post by yancek on 2014-07-18
> Ah I guess I didn't understand that part. But now I can't even access  the drive. When its in my PC the computer hangs at the motherboard  splash screen. 		

What happens when you boot with the external not plugged in and plugging it in after you boot?

---

### Post by vap1485 on 2014-07-18
Nothing. It doesn't spin up. 
It was working before when I plugged it into my hot swap bay....I dont think it died either because it only stopped working after I tried to change the permissions so Plex media server could access it. Im going to try the hot swap bay again

---

### Post by vap1485 on 2014-07-18
Hmm, I just thought of something, is there a way to 'scan for new hardware' since it's not coming up by its self, can I force it to see if anything is there?

---

### Post by Mark Phelps on 2014-07-18
> Nothing. It doesn't spin up. 

Drive is dead, then -- there is nothing you can do now.

---

### Post by vap1485 on 2014-07-18
well, I'll start the process for returning, as it's only a few months old. But do dead drives usually stop the computer form getting past the motherboard splash screen?

---

