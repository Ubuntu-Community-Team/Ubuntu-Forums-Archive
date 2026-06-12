---
title: "Partition/Install woes..."
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by jjcllhn on 2009-02-15
I'm trying to configure and install a dual boot XP/Hardy Heron system (with an eye towards future testing of Vista and/or Win7). 

AMD Athlon x2 64 4200+, Gigabyte K8N-SLI mobo, 2 MB RAM, new Western Digital 320 MB hard drive to replace a drive completely borked with Win virii. What I'd like to do is create 3 primary partitions (one for XP, two for future use) of 80GB each, and a logical partition to load Ubuntu 8.04 using the remainder of the drive. I've burned a LiveCD disk and verified it. I'm able to boot into Ubuntu from the CD-ROM, and run gparted. 

And that's when I hit the wall. I can create a virtual partition for the swap file, but I every attempt I've made to build either an ext3 or ext2 virtual partition in the remaining logical partition space has failed. Doesn't matter if it's the entire remaining space, the front, the back, or if I put the swap partition in the front or back of the virtual partition.  

Very frustrating, since I was planning to use Linux to recover the files from the infected drive once I get it installed (yeah, I know I should have backed up the data elsewhere, but it's the first time I've had data I wouldn't like to lose stored in Windows). 

Any help or comments appreciated.

---

### Post by Pumalite on 2009-02-15
Just shrink XP with Gparted and format what's left; ext3. Then install. Use 'Greater Free Space'. The installer will create a '/ partition and a /swap. You'll have Grub and dual boot.(unless you already have 4 primary partitions in your drive; in which case you have to take one of them and make an extended partition. Install Ubuntu inside. It will create 2 logical partitions: '/' and /swap)

---

### Post by wpshooter on 2009-02-15
I think you are limited to 3 or is it 4 primary partitions.

Do you already have XP installed ?  If not, you should consider installing XP first and then coming back to do the install of Ubuntu afterwards.

I would attempt to make a primary partition for XP, a primary partition for Ubuntu with logical partitions under that partition of /home and /swap and then make another primary for future installation of Vista.

However, if it were me, I would give up on that idea of installing anything that M/S makes and that way you do not have to be constantly worried about getting infected with viruses, etc.

Good luck.

---

### Post by CapnGimp on 2009-02-15
I have been multi-booting for years. MY partition method is...
 Only ONE primary partition of xGB for XP os only. Usually around 10-15GB

The REST of the disk I make and EXTENDED partion. Inside this I make multiple LOGICAL drives. One of these is a DOCUMENTS drive which I put 
"MY Documents" from windows. This allows you to toss all the things u usually do as a windows user here(pics, docs, music, etc. This prevents filling up the xp os drive with junk and allows you to keep it small. All other suff I have in other partitions. Any linux distro will be set up in this extended partition in their own logical drives.

 I also have a second drive with vista x64 on a logical partition with Ubuntu in the same extended partition.

 In my opinion you only need ONE primary. It simplifies later OS installations. Inside the extended partitions you can leave free space until you need a new logical drive. HOWEVER.... do yourself a favor and NEVER make a partition with VISTA, use linux, gparted, a live cd or xp.

 Vista doesn't adhere to atandards making partitions and it forks other osES.

---

### Post by Pumalite on 2009-02-15
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by jjcllhn on 2009-02-15
> **Pumalite said:**
> Just shrink XP with Gparted and format what's left; ext3. Then install. Use 'Greater Free Space'. The installer will create a '/ partition and a /swap. You'll have Grub and dual boot.(unless you already have 4 primary partitions in your drive; in which case you have to take one of them and make an extended partition. Install Ubuntu inside. It will create 2 logical partitions: '/' and /swap)

just to repeat: I have 3 primary and 1 extended partitions defined. Each partition is about 80 GB.

Partition 1 is NTFS, contains a working WinXP SP3. Primary use is gaming (for my kids), but I recently moved music, pictures and tax records onto the box (temporarily until I have enough money to build another PC). This PC had a 230GB drive that I have now replaced with a new 320GB drive. Given that I don't want to store my data under windows again, I was hoping to setup a dual boot box, and use the linux partition to recover my data from the corrupted old 230GB drive, and allow the kid to reload their windows games back into the XP partition.

Partition 2 is planned to be NTFS, will contain Vista at some point in the near future (I'm going to need it to do some testing for work)

Partition 3 is open presently. I anticipate the I will need it for testing Win 7.

Partition 4 is an already defined as extended (logical?) partition, this is where I want to install Ubuntu Hardy Heron. 

[QUOTE=wpshooter]I think you are limited to 3 or is it 4 primary partitions.[/QUOTE]

either 4 primary partitions, or 3 primaries and an extended partition (that can subdivided into multiple logical partitions) is the way I understand it.

[QUOTE=wpshooter]Do you already have XP installed ? If not, you should consider installing XP first and then coming back to do the install of Ubuntu afterwards.[/QUOTE]

Yes- XP Pro is already installed and working in the first primary partition. Upgraded to sp3, with anti virus/malware/ et al operational. Would love to harden the registry with group policies, but I'm not enough of a Windows admin to understand how to make that work in my home environment.  

[QUOTE=wpshooter]I would attempt to make a primary partition for XP, a primary partition for Ubuntu with logical partitions under that partition of /home and /swap and then make another primary for future installation of Vista.
[/QUOTE]
Got the windows part- I'm having gparted problems trying to create partitions for Ubuntu in the extended partition. 

[QUOTE=wpshooter]However, if it were me, I would give up on that idea of installing anything that M/S makes and that way you do not have to be constantly worried about getting infected with viruses, etc.[/QUOTE] My bad for putting my data on a box normally used by my kids for gaming, homework and surfing without a copy elsewhere. Sometimes temporary isn't as temporary as you'd like it to be.

---

### Post by jjcllhn on 2009-02-15
> **CapnGimp said:**
> I have been multi-booting for years. MY partition method is...
 Only ONE primary partition of xGB for XP os only. Usually around 10-15GB

The REST of the disk I make and EXTENDED partion. Inside this I make multiple LOGICAL drives. One of these is a DOCUMENTS drive which I put 
"MY Documents" from windows. This allows you to toss all the things u usually do as a windows user here(pics, docs, music, etc. This prevents filling up the xp os drive with junk and allows you to keep it small. All other suff I have in other partitions. Any linux distro will be set up in this extended partition in their own logical drives.

 I also have a second drive with vista x64 on a logical partition with Ubuntu in the same extended partition.

 In my opinion you only need ONE primary. It simplifies later OS installations. Inside the extended partitions you can leave free space until you need a new logical drive. HOWEVER.... do yourself a favor and NEVER make a partition with VISTA, use linux, gparted, a live cd or xp.

 Vista doesn't adhere to atandards making partitions and it forks other osES.

Didn't realize Vista could boot off an extended partition- my experience had been that most Microsoft OSs need to boot from primary partitions.

Plan was to reinstall the infected drive under Ubuntu, copy the data I need off, wipe the drive clean, define it as an extended drive that could be shared by any of the OSs launched from the first drive. 

I still don't understand why gparted is failing to create logical partitions in the extended partition, as I've outlined elsewhere in this thread. Are there known limitations to where the beginning/end of partitions must be located for it to work?

---

### Post by CapnGimp on 2009-02-15
AFAIK, there are no limitations on where, with gparted.

 Have you thought about Knoppix Live cd to just get your old data off the drive and put in a partition (data partition for either os) and then try reformatting the old drive from scratch and bypass this problem altogether?

 I am assuming the Ubuntu cd will not allow you to transfer the MS data presently for some reason?

 Back to the gparted problem u have now....
   I haven't EVER ran into a limitation with gparted 

                           UNTIL
  
    I tried to use it from a bad live knoppix cd. It had become scratched w/o my knowledge. I used this cd a bunch to resize partitions on computers with giant c drives(others) so I could show them linux.It would boot fine start gparted but when it came time to fialize/format, it failed. After a while, I figured that out, reburned a cd and it was fine.
 May not be your problem, but try another cd/dvd of live linux.

try Gparted Live cd  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
I'm hoping your version has a scratch I guess,  I hate crap like this haha
I was trying to install quite a few distros of linux on here lately and none would work. Ubuntu APPEARED to until reboot. THEN I found out about how VISTA made partitions were screwed. THATs why I couldn't install the others. I deleted the logical drives  I made with vista, and went from there.

 Good luck buddy.

---

### Post by CapnGimp on 2009-02-15
[http://ubuntuforums.org/showthread.php?t=1070710](http://ubuntuforums.org/showthread.php?t=1070710)

I posted this earlier. I learned a bit about MS bootloaders and Grub. 
 
 When you get bored check out the links for Vista boot process, I would assume windows 7 will be like it. I'm not doing windows 7, lol.
 I SAID I wasn't doing Vista, xp, 2k, I DID avoid all else but 95, 3.1 and dos haha.
 I have worked MS computers since 97 for people, for free. I am sick of polishing a turd. My buck stops here....or I should say, my pirate ship will sail no more into MS waters :lolflag:

HERE IS MY SETUP:


=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16faca8e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   159,284,474   159,284,412   7 HPFS/NTFS
/dev/sda2         159,284,475   903,045,779   743,761,305   f W95 Ext d (LBA)
/dev/sda5         159,284,538   318,568,949   159,284,412   7 HPFS/NTFS
/dev/sda6         318,569,013   476,262,989   157,693,977   7 HPFS/NTFS
/dev/sda7         476,263,053   635,547,464   159,284,412   7 HPFS/NTFS
/dev/sda8         635,547,528   794,831,939   159,284,412   7 HPFS/NTFS
/dev/sda9         794,832,003   840,054,914    45,222,912  83 Linux
/dev/sda10        840,054,978   840,231,629       176,652  83 Linux
/dev/sda11        840,231,693   898,643,969    58,412,277  83 Linux
/dev/sda12        898,644,033   903,045,779     4,401,747  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9afd9af

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    63,488,879    63,488,817   7 HPFS/NTFS
/dev/sdb2          63,488,880   976,768,064   913,279,185   f W95 Ext d (LBA)
/dev/sdb5          63,488,943   222,773,354   159,284,412   7 HPFS/NTFS
/dev/sdb6         222,773,418   382,057,829   159,284,412   7 HPFS/NTFS
/dev/sdb7         382,057,893   541,342,304   159,284,412   7 HPFS/NTFS
/dev/sdb8         541,342,368   700,626,779   159,284,412   7 HPFS/NTFS
/dev/sdb9         700,626,843   859,911,254   159,284,412   7 HPFS/NTFS
/dev/sdb10        859,911,318   976,768,064   116,856,747   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FE943B37943AF1AF" LABEL="SchniZZleZ" TYPE="ntfs" 
/dev/sda5: UUID="F0FC5CA5FC5C683C" LABEL="ISOz" TYPE="ntfs" 
/dev/sda6: UUID="74A8DFBDA8DF7BD4" LABEL="VISTA64" TYPE="ntfs" 
/dev/sda7: UUID="AA908DB8908D8C0F" LABEL="Vista soft" TYPE="ntfs" 
/dev/sda8: UUID="B480095380091D8C" LABEL="OVERDRIVE" TYPE="ntfs" 
/dev/sda9: UUID="7847ec12-adbb-4000-9d20-2b531c5261a9" TYPE="ext3" 
/dev/sda10: UUID="81ffa2ed-7ee2-4b8e-ae31-560a578797a3" TYPE="ext3" 
/dev/sda11: UUID="3fba05e2-83b7-4554-8c2d-005baf099ee7" TYPE="ext3" 
/dev/sda12: UUID="989ccfee-77ac-41ef-8cfe-6e3645ad79de" TYPE="swap" 
/dev/sdb1: UUID="80D018A2D018A088" LABEL="XPpro" TYPE="ntfs" 
/dev/sdb5: UUID="78A0D155A0D11B08" LABEL="Software" TYPE="ntfs" 
/dev/sdb6: UUID="36DCEE9BDCEE54A1" LABEL="Documents" TYPE="ntfs" 
/dev/sdb7: UUID="2EE00242E00210AF" LABEL="Games" TYPE="ntfs" 
/dev/sdb8: UUID="0EC01612C016011F" LABEL="Pictures" TYPE="ntfs" 
/dev/sdb9: UUID="842C405B2C4049FE" LABEL="MUSIC" TYPE="ntfs" 
/dev/sdb10: UUID="581C665A1C6632E4" LABEL="Vista games" TYPE="ntfs" 

=============================== "mount" output: ===============================

---

### Post by caljohnsmith on 2009-02-15
Jjcllhn, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```

---

### Post by jjcllhn on 2009-02-15
I'm beginning to suspect there's something wrong with the CD drive.

Just downloaded 8.04-desktop-i386.iso, validated the MD5 checksum.

Burned the image on the CD drive at 8x, rebooted to the LiveCD, ran the check image, and there's 1 bad file. All this without removing the LiveCD from the player. Still boots to Ubunutu, set the partitions to 2 primary (both NTFS, 80GB) + 1 unallocated extended partition of 160GB. Ran installer, selected "guided install to largest unallocated partition" rather than the manual install, it selected the third partition, started the install, made it to the 22% mark before informing me the globber file is corrupt and terminating the install.

At this point I'm going to find an alternate CD writer to burn the CDLive and perform the install.

Thanks to all for the help, and the links.

---

### Post by jjcllhn on 2009-02-15
> **caljohnsmith said:**
> Jjcllhn, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf231f231

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163846934    81923436    7  HPFS/NTFS
/dev/sda2       163846935   329573474    82863270    7  HPFS/NTFS
/dev/sda3       329573475   625137344   147781935    5  Extended

killed one of the primary partions, created one large extended partition without logicals for type 3 install (guided install to largest unallocated partition.)

Now using a USB CD-RW Drive to burn Ubuntu LiveCD, and boots up fine (i'm posting from the live boot). going to try the install now.

---

### Post by caljohnsmith on 2009-02-15
How about when you are on your Live CD, open a terminal (Applications > Accessories > Terminal), and then do:
```
gksudo gparted
```
That will open gparted from the terminal, and the advantage of that is you can easily see which errors gparted reports. So using gparted, if you right-click the unallocated space in your extended partition and select "New", and then use that to create a logical partition in the extended partition, what is the exact error that you get?

---

### Post by CapnGimp on 2009-02-15
As far as BURN SPEED when you are making iso cd/dvds.... BURN SLOW!!

 SOMETIMES it causes problems burning fast.
 I went thru about 30 DVDs over a period of 1 week, using FOUR different computers with different burners in each, linux and xp on each computer failed to burn correctly. I was trying out Sabayon linux couple years ago.  I had never had a burn failure to this point with isos.

 I had to burn at 2x to get it right. 
I was burning SuSE 11 a few days ago and ran into the same problem. Burnrd at2x and it is fine.

 I bought different media brands and types also.
 It came down to SLOW burn speed. Nothing else.


 Oh yeah, when doing Ubuntu the other day, It would not 'Use free space"   tried the entire drive regardless. I finally made a boot, /root, /home and swap manually. Then spent the next 24hr+ figuring out how to get xp, wista64 and Ubu to play well together, lol.

---

### Post by jjcllhn on 2009-02-15
I'm up!!!

Did the burn/install with an old external Plextor USB CD writer, rather than the internal DVD/CD device.

Install went smooth as silk - kinda like I was hoping for about 24 hours ago.

Now on to the recovery...

And thanks again.

---

### Post by CapnGimp on 2009-02-16
Congrats! Now if ya need help on recovery, I'm no expert but I have a fair amount of experience using free tools from windows. I have yet to do it from linux, sounds like a project for me, lol.
 
here is what I have used over the last few years.
[http://www.pcinspector.de/Sites/task_manager/info.htm?Language=1](http://www.pcinspector.de/Sites/task_manager/info.htm?Language=1)
 get the one for hard drives.

---

