---
title: "Trouble installing XP or Ubuntu on a  Averatec 2200"
date: 2009-03-06
forum: Hardware
---

### Post by X_X_loaded_X_X on 2009-03-06
My goal is to dual boot XP and Ubuntu on a used Averatec 2200 Laptop. I have had some experience with Ubuntu but an still very new to it. I am really good at windows and mac based sutff and hardware...but this issue lol..is driving me crazy.

Its decent AMD 64/512MB/80GB IDE/DVD RW. The person I got it from windows install was bad. It would get the black select screen and wouldn't load normal, last good config, safe,etc. I ran a Ubuntu 8.04 to grab the drivers out of a folder on C: The hard drive seemed good all data I was able to open and it wasn't corrupt.I had Ubuntu running for a while so there seemed like no hardware issues.

Seem so far like a normal windows install...Wrong.. So I tried to reinstall Windows XP Pro SP3. It was just restarting during the install.  So it decided to load hirens boot cd 9.7 and just wrote zeros to the drive. It would still restart when it get to the part where you finish loading all drivers and have to press F8 to accept terms. I never got to where you select the hard drive and format and install. So being annoying I ried to load Ubuntu 8.04 it gave me an error it couldn't access the hard drive. The hard drive the whole time is viewable in the BIOS it is changeable in boot order. I reset the bios to defaults.

I restart Hirens boot CD and ran PC Doctor 2004 the hard drive test the controller failed, all other testes passed. I tried a known good 20GB IDE Drive and it had the same issue as the 80GB not loading XP and restarting.

Now it gets strange. I loaded hirens boot CD and every program can read, write, format partition the drive. I ended up using a few tools to repartition it and in the end used Acronis disk director to split it in half one fat32 partition and one NTFS partition. I dont know why just though XP install might pick it up.

XP still wouldn't work same is as before. Then I got an message "memory overflow error" I googled it alot seems to relate to bad install discs and bad memory. The XP CD is good I even tried 2 known good XP Pro discs and a OEM XP home disc all with the same results as above.

So now I try to load the dreaded Vista lol. The original drive is still in and the partitions are still the FAT32 and NTFS split. Vista wont install on the NTFS partition and the FAT32 because its FAT32 duh. So I tried to format the FAT32 and it just hung. I powered it off and it came back up the FAT32 was unallocated and the NTFS was in tact. I erased both then tried to format.. it hung I powered it off then went to bed.

I guess next I am gonna try to load from USB. I would appreciate any help, suggestions, work a rounds.

 Thanks in advance for any help.

---

