---
title: "Primary Master IDE Drive Failed - Lookingfor Data"
date: 2014-03-18
forum: Hardware
---

### Post by jim46 on 2014-03-18
Client has "Linux" system, he has no idea what variety.  HDD failed after office relo. Primary Master IDE was Maxtor 120GB, Primary Slave is Seagate 120GB. Secondary Master is CD/DVD, Secondary Slave is Hitachi 123.5GB.  I've installed a temporary 20gb drive.  I ran server 12.04.4 server 32bit setup. When asked to select the disk to install to I see the 20gb as SCSI (0,0,0) sda NTFS, SCSI1 (0,1,0) as sdb RAID, and SCSI2 (0,1,0) as sdc EXT3.  

I only need the user data.  I can rebuild the system with Ubuntu, but don't want to overwrite anything needed.

I've ordered a replacement drive, but don't have faith the owner is correct on the disk usage.  Either the lone 123.5gb drive was the boot drive or the two mirrored 120gb drives were  I'm guessing they were together only because of the similar capacity.  User thinks the RAID was for data storage.  

How do I determine which physical drive was the boot drive?

How can I recreate the mirror?

Should I be using rescue mode?  I see that I can "assemble raid array" from there.

I am unable to mount the drives from the ash shell during install.

Thank you in advance.
Best regards,
Jim

---

### Post by jimbean on 2014-03-18
when i try to save data from old drive i will boot new system with old hd attached as slave to new hd as master if there is no constant clicking from old drive you can probably rescue anything

---

### Post by jim46 on 2014-03-19
@jimbeam - my issue is that I don't know which drive has the data.  Should I do a new install to the temp 20gb drive and then mount the 120gb & the 123.5gb drives to view them?  Should I wait for the replacement drive and then attempt to rebuild the mirror?  What should I look for to insure I don't overwrite them during install?

Btw... I've tried to query the drives on a Windows systems via DiskInternals utils in an external USB chassis with no positive results.

Thanks.
Jim

---

### Post by grahammechanical on 2014-03-19
My guess that the drive with Linux on it is sdc Ext3. I think that you are complicating things by putting in that temporary 20Gb drive. You know what that drive is and what it is there for. Even if you install Ubuntu server into it and use it to rescue the data it will be removed and you will need to put in the new drive and install Ubuntu into that. What drive will the new drive be replacing? 

My guess that it should replace sdc which has the Ext3 Linux file system which was the default Linux file system a few years ago. 20 GB should be more than adequate for a Ubuntu installation and it gets the client back in business until the new disk arrives and you start all over again.

Regards.

---

### Post by jim46 on 2014-03-19
I think I have caused some confusion here.  The system I have lost a 120gb drive and does not boot. I see now that I failed to mention the system does not boot, no matter which drive I attempt to boot from.  This drive was allegedly part of a mirror with, I presume, the other 120gb, based on the "RAID" filesystem notation on that drive.  The client believes the raid drive was for data and the third drive, the 123.5gb drive with ext3 FS, was for the OS.

I think there is more than one issue here.  If the ext3 drive was the boot drive, why doesn't it boot?  And, why doesn't the mirror work in the expected degraded mode?

I installed the 20gb drive purely to interrogate the other drives for contents.  The drive is an old one and I don't have confidence in providing it to the client.  Should I do a temp install to this and put /root on it, then "mount" the other drives read-only to interrogate them?  Eventually, the replacement drive would become part of the mirror set.

So how do I confirm the ext3 drive was the /root drive?

When I install the final replacement drive, how would I rebuild the mirror, as that likely has the client's data that we wish to recover?

Thank you all for taking the time to assist.
Jim

---

