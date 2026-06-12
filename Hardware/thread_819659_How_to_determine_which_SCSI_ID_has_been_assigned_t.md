---
title: "How to determine which SCSI ID has been assigned to which SCSI Device"
date: 2008-06-05
forum: Hardware
---

### Post by Ted_Smith on 2008-06-05
Hi

I have a machine with a 410Gb Hardware RAID concisting of 3 SCSI Hard Disk. I then have the OS drive (Fujitsu disk) which is another SCSI Disk that is not part of the RAID array. Lastly, I have a 120Gb Seagate SCSI Disk connected via LV\SCSI on a seperate cable that acts as a slave storage facility. I have a DVD drive connected via IDE. 

I have a SCSI card for external SCSI devices that currently has nothing connected to it. 

I want to determine which SCSI devices (cards, disks, RAIDs etc) have got which SCSI ID's assigned to them so that when I attach my next SCSI external device I know what ID to assign it with regards to the optimum assignment method of SCSI IDs (i.e. 7 being the highest priority usually given to the card, 6 the next highest, 5, 4, 3, 2, 1 0 then 15, 14, 9 and 8. 

I want to ensure my OS disk, hardware RAID and their controllers have the highest priority ID's with the external card and external devices having the lowest priority. 

I have used lsscsi which shows me the following : 

[0:0:0:0]    disk    DELL     RAID_410Gb       V1.0  /dev/sda

[0:1:0:0]    disk    SEAGATE  ST3146807LW      DS09  -       
[0:1:1:0]    disk    SEAGATE  ST3146807LW      DS09  -       
[0:1:2:0]    disk    SEAGATE  ST3146807LW      DS09  -       

[1:0:0:0]    disk    FUJITSU  MAP3367NP        5605  /dev/sdb

[1:0:2:0]    disk    SEAGATE  ST3146807LW      DS04  /dev/sdc

[3:0:0:0]    cd/dvd  LITE-ON  DVDRW SHM-165H6S HQSA  /dev/scd0

but I don't really understand how the ID assignments are showing? 

Thanks

Ted

---

### Post by sdennie on 2008-06-05
Have you had a look at the lsscsi man page?  That might help you understand what you are looking at:

```

man lsscsi

```

Edit:
You could also look at /proc/scsi/scsi.  That presents the info a nicer way.

---

