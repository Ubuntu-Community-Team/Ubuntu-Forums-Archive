---
title: "How to troubleshoot an old HDD"
date: 2014-01-16
forum: Hardware
---

### Post by mastablasta on 2014-01-16
I have a very old maschine from 1997 or 96. the box was upgraded quite a bit. it had windows installed (first 98, later xp) and ended with:
AMD64 3200+
1GB RAM
128mb ATI Radeon 9200

it has two disks one is the _***original***_ 10 GB ATA disk (where Windows used to live on 5GB disk space :P ). And another 160 GB disk where i kept data. both disks were FAT32 formated. FA32 goes up to about 128GB so the newer disk had some unformatted space where i intalled Kubuntu.

the original OS had some issues. first i couldn't get it to use new WD drive which was supposed to replace the old 10GB drive. it just kept on rebooting or would only boot occasionally on that disk.

we never could figure out if it was hardware or software issue. later computer started to have random reboots and crashes eventhough it was stable before so we got a new one. but some more maintenance showed that there is some malware installed on maschine. we purged malware from windows, then from 2 live antivirus discs. last one found substantial number of infected files and everything was removed. i then installed Kubuntu on free space (different disk).

it gave me problems as i could not put the grub on the windows boot disk. it only wrote half of it and then stopped. ok, so i put grub on data disk. here is where things go strange - 
first linux didn't see any partitions on windows disk. ok, i thought partition table got corrupted. 
then after a couple of boots the disk dissapered from linux. it wasn't available to mount.

how would i troubleshoot this disk from linux? how would i run the diagnostics? which programs exist for this if disk is non SMART? i am not sure if it's smart capable since it is so old. the data is backed up but i would like to see if disk i actually ok and if it is i would like to get the windows working again and create dualboot for some LAN games. linux support for Radeon 9200 isn't really stellar :-)

---

### Post by tgalati4 on 2014-01-16
Burn your self a copy of Ultimate Boot CD (UBCD) and use that to check the disk with the manufacturer's utility.  The crashing could be a power supply or motherboard problem.  Check the capacitors to see if they are bulging or leaking.

---

### Post by mastablasta on 2014-01-16
PSU is new, capacitors are ok i already checked them. in fact so far Kubutnu works normal. i haven't used it so much since i do not live there anymore but whenever i did use it, it didn't crash. so far it all points to software issue.

i already downloaded the ultimate boot cd. i will see how it goes. i am hoping the disk is SMART since there are plenty of tools for those. otherwise i think disk is/was hitachi, so hard to say if Htachi really made it or soemone else. we'll see how it goes.

---

### Post by Bashing-om on 2014-01-16
mastablasta; Hey ;

Elementary, but, The simple things are often overlooked. Have you updated bios ? - A lot has changed in 10 years or so -

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by mastablasta on 2014-01-17
hard to say if BIOS got an update. the thing is i was working on it as well as my brother who lives there. i think he did update and performed a number of troubleshootings with that new disk. but i am not sure. it's a good point. i need to check that. i never try to "fix " what is already working. 

the new disk (750GB one we tried to add there) is now used in another maschine. it is now EXT4 formatted and seems to be working. so yeah it could be BIOS or it could also be poor SATA cable. hard to say for this one. as i remember system occasionally booted normally but would also sometimes hang on this disk. tried it all on the new disk, cloning, fresh install... well we'll see what happens when i run some diagnostic tools. i think this is the 4th mobo in the box. LOL first one got bulged capacitors issue ( :-( ) second one got P2-400 upgraded to intel Celeron 1600 Mhz using special interface (i wonder if they sitll make something like that for these new CPU's). anyway win98 just flew on that setup (256MB ram, 1600 celeron, 16MB ATI rage). then came the third mobo which failed completelly. and now it's 4th mobo which i gave from my maschine to accomodate the AGP card. 

the computer has nice PSU and large fans so it is reasonably quiet. i am thinking we could use it as server. the power usage on these athlons is not so bad and threy are not slow either (for some simple home server). ATI card is fanless and is actually not that bad. ok nothing compared to new ones but it can still play a game or two.

---

### Post by Bashing-om on 2014-01-17
mastablasta; Wow, that old box has been around - and still performing.

I have an old AMD sempron box with a similar story. In it's next reincarnation it will have Athlon CPU and better Nvidia graphics.

The reason I point to bios updates, in my hazy memory, older bioses would only boot a harddrive as the 1st drive.

Just a thought.
Not that I am teaching grampaw  how to suck eggs.

---

### Post by mastablasta on 2014-01-18
heh. i also have a win95 maschine - 486 DX2/80 Mhz with 32MB ram and 850 Mb hard disk. it's still working but i think PSU has issues on that one and i know that battery for clock is dead (i think it got stuck on the 90's).

anyway back to the more usable one. i ran ultimate boot CD and it found the drive. The drive is SMART capable.

It's a Fujitsu MDP3108AT 10 GB. i ran diagnostics tests on it with manufacturers tools as well as some other tools. all tests including comprehensive one were good. Disk seems to be in a good condition even after so long. i am impressed. i couldn't run any diagnostics from linux partition, since it just doesn't see the disk. i tried KDE partition manager (same thing as gparted) and it doesn't see it. 

but i know i saw it in that parition manager, so i boot the live DVD and sure enough i can see it there. hwoever it seems parition table is corrupted (it says no partition table). so now i think i need to somehow fix the FAT32 partition table on it. i believe it could have been corrupted by either a malware or by the virus scanner being too agressive in the cleanup. my bro said it was late, so he just told it to delete whatever it found :-D.

is there a linux tool to fix FAT32 partition table (i guess this can only be done in live session since in normal Kubuntu the drive is not seen) or does anyone know if there is such a tool on Ultimate boot CD? ugh i guess i need to dig into that old thick DOS book again...

---

### Post by Bashing-om on 2014-01-18
mastablasta; Hey; 'nother thought,

Though highly unlikely ; How bout "meta data" imposed on that disk ? Would not take long to down load the dmraid tools and take a look.

I am aware there exist some limited abilities within linux to test NTFS, do not recall anything about linux's ability in fat32 testing.

If all else fails, swap the ribbon cable out ? OH yeah !, Bit me more than once, check the pinning on the hard drives - slave, master, cable select (is cable select supported ?) 

That drive is good ->
[INDENT][INDENT][INDENT]gotta be a way
[/INDENT][/INDENT][/INDENT]

---

