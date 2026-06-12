---
title: "Half mounting, half software problem &gt;&lt;"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Death Rider on 2007-10-31
Hi, the problem I am experiencing is that I have 3 HDDs. 1 of them is old and not suitable for everyday use, because it has some problems, which I am not going to discus, but still it is useful when I want to play with linux. As you know it takes lots of time and I'm quite busy.
What I wanted to say is that Windows has gone crazy again so I decided that it's time to rewindow my PC. It has 2 HDDs. One is 230Gb and the other is 150. I unpluged the 150 and put it aside for the moment. I create a 50 Gb partition for windows and what is left (230-50=180gb) is for programes, games and other suff. So whenever I need to reinstall windows I simply format those 50 Gb. I used to use KIS (Kaspersky Internet Security) but it's really tough. I decided to go for Nod32+Zone Alarm Internet Security (has AV in it but you can disable it during the instalation). Now while logging in windows freeze. Now it doesn't even reach the user account choosing menu... So I decided to make copies of my documents and format those 50 Gb again. I loggend in to my Ubuntu, saw those two partitions (50&180) after pressing Computer. I clicked on them and they got mounted automatically for me to access. Later on I found a way to be able to delete files in NTFS partitions via ntfsfix, NTFS configuration tool and by force mounting :P I deleted ZoneAlarm's files in system32 so that it could not scan anything when the PC is starting, but I get the same black frozen screen... I redid the HDD pin settings again and booted up Ubuntu, but, not for the first time, the NTFS partitions were nowhere to be found... I used sudo lshw -C disk to get some info and here's what I've got:
  *-disk:0                
       description: SCSI Disk
       product: SAMSUNG SP80A4H
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sda
       version: RT10
       serial: 0471J1FTC01218
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@4:0.0.0,1
          logical name: /dev/sda1
          capacity: 71GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@4:0.0.0,2
          logical name: /dev/sda2
          size: 2925MB
          capacity: 2925MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 2925MB
             capabilities: nofs
  *-disk:1
       description: SCSI Disk
       product: WDC WD2500JB-00G
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/sdb
       version: 08.0
       serial: WD-WCAL78071285
       size: 232GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: HPFS/NTFS partition
          physical id: 1
          bus info: scsi@4:0.1.0,1
          logical name: /dev/sdb1
          capacity: 48GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@4:0.1.0,2
          logical name: /dev/sdb2
          size: 184GB
          capacity: 184GB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: HPFS/NTFS partition
             physical id: 5
             logical name: /dev/sdb5
             capacity: 184GB

As you can see the partitions are named /dev/sda1, /dev/sda2 and there smth else about /dev/sda5, but i don't understand what it is :/ I tried mounting these on  /media/Antras/, tried to enter the folder and got this:
**The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "Antras".
Can someone please help? :/

---

### Post by Death Rider on 2007-11-01
:confused: Bump :confused:

---

### Post by dabl on 2007-11-01
I'm not sure how many problems you may have tangled up there ....

First, unplugging a hard drive while installing Linux, and then plugging it back in and trying to patch up the results tends to work against the ability of the installer to detect and configure the system for you -- it's like "SURPRISE -- WHAT AM I?" to the OS.  So you didn't help yourself doing that.

Second, Linux (more than Windows) is totally depending on a fully-functioning hard drive and filesystem.  So whatever issues you're having with Drive #3 that is "not suitable for daily use" aren't helping this picture.

Third, it appears you have both /dev/sda1 and /dev/sdb1 set as "bootable", if I understand the output correctly.  Linux theoretically doesn't require a boot flag to be set, HOWEVER, it takes its cues from BIOS about the hard drives, and BIOS definitely does detect boot flags, and of course Windows requires a boot flag to be set where its MBR resides.  Soooooo, I dunno about that situation, but my personal rule is to have a maximum of 1 bootable partition on a PC.

Finally, is that Samsung drive one of the new "vertically magnetized" or whatever that new recording technology is?  I've seen reports of trouble with that line of Samsungs.  You can review the dmesg output and see if there are errors during the characterization of that drive.

That's all I can offer at the moment with what I see in your post -- sorry it can't be more upbeat.  :(

---

### Post by Death Rider on 2007-11-01
Hm... Installing Linux was quite successful. The thing is that I'm quite afraid of it. It's really different from windows which I am used to. That's why I can't move to Linux, but I noticed that Linux ALWAYS has a solution, unlike windows :D

The "not suitable for daily use" doesn't mean that it has problems operating :P The problem is this: When I delete something in this HDD via windows, the file disappears but no additional free space appears, so you end up having full HDD and no files :D I know it's a problem with some file in the hdd that controls this, but I don't know how it's called. I really wanted to try Linux, so I thought that this old HDD might be of some use :) And it is. I am not going to fill it up with music, movies and any other heavy stuff. Just Linux programs :)

Third answer: If i hadn't tried GParted just a few minutes ago, I might have had a problem understanding your comment. Now I found out a few things: Linux and Windows really do have a boot flag on them. Windows doesn't run and I will probably just overwrite a fresh copy on top, make backups, format windows and reinstall them :) The other thing that I saw is that Linux does see my other HDD. I was able to see it's partitions.

Actually, SAMSUNG is one of the worst HDD producers on the list, while WDC are one of the best ones ;)

Please follow this link to enter my other topic, where I ask a few questions that are similar to this topic and a few new ones:
[http://ubuntuforums.org/showthread.php?p=3686656](http://ubuntuforums.org/showthread.php?p=3686656)

---

