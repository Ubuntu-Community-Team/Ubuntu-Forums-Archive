---
title: "Messed up RAID1: can I recover data?"
date: 2008-10-07
forum: Hardware
---

### Post by maxxum on 2008-10-07
I had two drives, lets call them drive1 and drive2 set up as RAID1 mirrored array in my Gigabyte BIOS. They were both NTFS formatted and were used mostly in Ubuntu. After some time I realized that I cannot move the drives to another computer or I wouldn't know what to do in case the motherboard dies so I decided I do not want to RAID them, but I will do manual backups. So I changed the BIOS setup such that the SATA controller was not in RAID mode anymore. Then I removed drive2 and kept it as an external drive.
After a while I learnt about mdadm, the Linux software RAID system. I figured this makes the RAID array portable and I do not need to worry about manual backups. So I got another identical drive, drive3 and formatted it and drive2 into ext3 volumes under mdadm RAID1 array. They both got some data from drive1 and are working fine as an array as of now.
One day I had to clear my CMOS and that reset the BIOS. I forgot to keep the SATA controller in a non-RAID mode. Now it remembeted the old RAID1 array I had created in the beginning. It started reporting a degraded RAID array and asking me to rebuild it. I didn't rebuild but I saw that the drive1 (the ntfs volume which still had some non-backed up data) is not mounting anymore. It worked for a few days though but now it didn't. I booted into xp (64bit) and it couldnt mount the drive. It says it is either corrupted or unreadable. It seems that the RAID controller of BIOS wrote something to the drive1's sectors. I tried connecting it as an external drive in my laptop which is running Ubuntu 8.04 as well. It said
```
 mount: unknown filesystem type 'isw_raid_member' 
```

When I try to mount it on my desktop Ubuntu, it says that it required the type of partition to be mentioned. When I mention -t ntfs option, it gives me an error:
```
Failed to mount '/dev/sde1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```
This is different from what my laptop's Ubuntu sees the drive as. Booting into windows and running chkdsk /f DriveLetter: does not work as windows cannot read the partition type data. It seems that the partition type is indeed isw_raid_member as reported by the laptop.

Question is: how can I reset the sector on this drive without losing data so that this drive becomes the normal NTFS drive?
Update: I tried using TestDisk software. It shows that both MFT and its mirror are corrupt. :confused: It says you should use some commercial software to recover data in this case. I am not sure if the data is irretrievable yet. There must be some way out...??

---

