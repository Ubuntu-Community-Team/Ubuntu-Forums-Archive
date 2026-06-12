---
title: "External Hard Drive Problem"
date: 2012-08-18
forum: Hardware
---

### Post by Dalek Draco ON LINUX on 2012-08-18
I have an external harddrive (interal drive in a case connected via usb) and it has been working fine. I've gone to connect a few days ago and nothing showed up anywhere (not in disk utility/system monitor/desktop etc).     I logged in on windows and the device showed up but I couldn't access anything, and it was messing up a fair bit.   Went back to ubuntu and tried again, and I get the following error message:   

Error mounting: mount exited with exit code 13: The disk contains an unclean file system (0, 0). The file system wasn't safely closed on Windows. Fixing. ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.    

I'm happy to lose all the data, I've backed most of it up, but I need the harddrive as a backup source so I need to format it. Atm whenever I connect I can't do anything (including formatting) until it eventually gives the above error message and the drive disappears until I reconnect.  

Please HELP!!! lol

---

### Post by carl4926 on 2012-08-18
Such devices must be 'safely removed' in windows or they become what is termed 'Dirty'.

You may need to use windows to repair the drive too.

I gave up using ntfs a long time ago, but I don't use windows either

---

### Post by Dalek Draco ON LINUX on 2012-08-18
Thanks for your reply.  Would you happen to know what I'd need to do in windows to repair the drive? I don't seem to be able to do anything to it whilst in Windows.

---

### Post by oldfred on 2012-08-18
Did you run chkdsk? And you may have to run it multiple times as it does not always fix everything on one pass. Rerun if any errors the first time.

---

### Post by darkapec on 2012-08-19
if you are happy to loose all the data then I would just install gparted on your ubuntu machine and reformat the drive to FAT16 or FAT32, you will run into less corruption issues this way. 

have you tried running fsck on ubuntu yet? Or is that not possible?

---

### Post by carl4926 on 2012-08-19
> **Dalek Draco ON LINUX said:**
> Thanks for your reply.  Would you happen to know what I'd need to do in windows to repair the drive? I don't seem to be able to do anything to it whilst in Windows.


command prompt

```
chkdsk /f
``` IIRC

---

### Post by Dalek Draco ON LINUX on 2012-08-19
@Oldfred- chkdsk kept freezing when I tried to run it on the harddrive and wouldn't start responding again until I unplugged it.  

@darkapec- I've just tried to run it in GParted and reformat, it just seems to hang there without doing anything. However when I look at it in disk utility (GParted has been left to run) its showing 1 of the 3 partitions on the harddrive changed to ext4 (which is what I set them to reformat as). So it's possible that it's working and just taking a while. I shall leave it for an hour and come back and see.   Thanks for your help so far.

---

### Post by Dalek Draco ON LINUX on 2012-08-19
Thank you darkapec! 

Not sure why I didn't think of using GParted before, but it's done the trick. I reformatted the three partitions to ext4, and then jumped in to disk utility to reformat the drive into one partition. 

Given that I need to store files larger than 4gb on the harddrive (bluray movies) I'm going to look at what format would be best before I start loading all my data back on to the drive.

Thank god I've been paranoid lately and had a mirrored backup of the drive on another drive :P.

Thanks again.

---

### Post by darkapec on 2012-08-19
if your formatting to ext4 how is windows going to read it? Is there some tool you can install to make windows detect such formats? I believe exfat would be the only format that would go both ways and still allow you to hold files over 4gb. 

Glad gparted solved your problem

---

### Post by Dalek Draco ON LINUX on 2012-08-26
I don't need Windows to read it. I'm only running Ubuntu. I don't know of any tools that will allow windows to read ext4, but there might well be some.

Thanks again.

---

