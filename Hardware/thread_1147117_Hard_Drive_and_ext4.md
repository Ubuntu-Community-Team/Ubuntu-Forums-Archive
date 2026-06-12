---
title: "Hard Drive and ext4"
date: 2009-05-03
forum: Hardware
---

### Post by VladNistor on 2009-05-03
Hello,

Background info:
I used to have a dual-boot system (Vista & Jaunty). Then my Windows broke and I decided to get rid of it. Copied all my data to another partition (ntfs->ext4). During the copy process I got several I/O read errors on 4-5 files. Didn't think much of it at the time and reformated the ntfs partition to ext4.

HW info:
```
description: ATA Disk                                                                                                          
                product: SAMSUNG HM251JI                                                                                                       
                physical id: 0                                                                                                                 
                bus info: scsi@0:0.0.0                                                                                                         
                logical name: /dev/sda                                                                                                         
                version: 2SS0                                                                                                                                                                                                                       
                size: 232GiB (250GB)                                                                                                           
                capabilities: partitioned partitioned:dos                                                                                      
                configuration: ansiversion=5 signature=000aXXXX
HDD age: 3 months 
```Now:
The read errors seem to have spread from the ntfs partition to my other ext4 one, while still affecting the newly formatted ext4 (the one that used to house windowz).
Torrents give errors while downloading, files can't be read, movies can't be read (those stored where the files with the errors used to be).

My attempts at solving this:
I tried running fsck on bothe ext4 partitions. The result was that they were allright, but it only did an innode check. I used the -c option to make it look for bad sectors, which I thought was the problem, but the operation hangs at 26% after running for less than 2 hours out of the 8 i was away from my computer.
I've enabled S.M.A.R.T. on my HDD and it reported 54 bad sectors, but I think there are more or S.M.A.R.T never told Ubuntu where they are so it keeps using those sectors.

What SMART says about my HDD:
```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:  
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       11614    
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2687     
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       309      
  5 Reallocated_Sector_Ct   0x0033   010   010   010    Pre-fail  Always   FAILING_NOW 844      
  7 Seek_Error_Rate         0x000e   252   252   051    Old_age   Always       -       0        
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0        
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       1915     
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0        
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       205      
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       1191     
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       116      
194 Temperature_Celsius     0x0022   115   079   000    Old_age   Always       -       41 (Lifetime Min/Max 15/55)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       11799                      
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0                          
197 Current_Pending_Sector  0x0012   095   090   000    Old_age   Always       -       54                         
198 Offline_Uncorrectable   0x0030   252   100   000    Old_age   Offline      -       0                          
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0                          
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       279                        
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0                          
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       429                        
225 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       37926 
```What do you recommend I do next? Get a new HDD? Call Samsung?
Is there a way to get fsck to not hang? Do you recommend an alternative to fsck?

---

### Post by mikedep333 on 2009-05-03
You're best off backing up as much of your data as possible to another drive, and then buying a new drive.

You may need to run Ubuntu off of a live CD/USB-key in order to reliably access your drive.

I have had success in the past with repairing drives with I/O errors by running a low level format. Either [DBAN]("http://www.dban.org/") or the ubuntu utility "wipe" will work. Of course, you will lose all your data by doing that, and I don't know if that will work when there are SMART errors.

---

### Post by VladNistor on 2009-05-03
Thanks mikedep333, I'll probably be doing that unless someone has a better idea. The only way I could back up my data is writing it to a CD/DVD, but I'm afraid the I/O errors will make that impossible.

Since posting I've tried the following:

1. Use Gparted to format the (old ntfs/new ext4) partition.
I got a black screen while the format was underway and had to do a hard reboot (ctr+alt+sysrq+b).
My Bios no longer recognised my HDD.

2. I booted a 8.10 livecd and tried to format the partition to ext3.
The partition was set as Unknown. I attempted to format it to ext3 and it failed saying it can't read the disk, then Gparted said there was no disk present.

3. Reboot
I can now access the HDD and have succesfully booted into Jaunty again. The partition is still Unknown but everything else works.

Does anyone have any other ideas? 

Thanks in advance!

---

### Post by mikedep333 on 2009-05-03
If the bios no longer recognizes the hard drive after doing stuff, that's a very bad sign for the drive.

And with I/O errors, it's far easier to backup files to USB drives or network shares, so that you can skip copying files that there are I/O errors for. I can help you with network shares if necessary.
[https://help.ubuntu.com/community/SettingUpSamba#Browsing%20SMB%20shares](https://help.ubuntu.com/community/SettingUpSamba#Browsing%20SMB%20shares)

---

### Post by HavocXphere on 2009-05-03
> **VladNistor said:**
> I've enabled S.M.A.R.T. on my HDD and it reported 54 bad sectors, but I think there are more or S.M.A.R.T never told Ubuntu where they are so it keeps using those sectors.

1. When SMART starts reporting errors then the drive is about to die....because SMART is usually pretty late in catching on.

2. HDDs mostly regulate bad sectors on a hardware level, so it won't really "tell Ubuntu about them". It transparently shuffles info around since even a working hdd gets occasional bad sectors. (There are "spare" sectors on all hdds)

---

### Post by VladNistor on 2009-05-04
Thanks for all your help guys!

I will try the low level format in a couple of weeks when I'm less busy, have time to look for a new HDD if it breaks after that operation or if the operation fails, and can get my hands on an external HDD to back up my data.

There are two further questions I have:

1. As explained, my first ext4 partition became "ill" after I copied the files from my then NTFS partition onto it. Is that even possible? I wouldn't want to destroy an external HDD by copying files to it. (It sounds absurd that one partition could inflect another and I've never heard of it, but I'm not a HDD expert so I'll ask).

2. Is there a way to do a low level format of a single partition?

I'm still open to other suggestions and would like to hear more opinions on the matter. Thanks again to mikedep333 and HavocXphere for their help.

---

### Post by mikedep333 on 2009-05-05
> **VladNistor said:**
> Thanks for all your help guys!

I will try the low level format in a couple of weeks when I'm less busy, have time to look for a new HDD if it breaks after that operation or if the operation fails, and can get my hands on an external HDD to back up my data.

There are two further questions I have:

1. As explained, my first ext4 partition became "ill" after I copied the files from my then NTFS partition onto it. Is that even possible? I wouldn't want to destroy an external HDD by copying files to it. (It sounds absurd that one partition could inflect another and I've never heard of it, but I'm not a HDD expert so I'll ask).

2. Is there a way to do a low level format of a single partition?

I'm still open to other suggestions and would like to hear more opinions on the matter. Thanks again to mikedep333 and HavocXphere for their help.

1.I've seen weird links and files get placed on windows partitions, but copying files normally cannot cause I/O errors unless the drive was developing hardware problems on its own.

2. You can use wipe on a single partition, such as /dev/sdb2 , rather than the entire drive, such as /dev/sdb .

---

