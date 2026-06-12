---
title: "WD HDD TB1 - Issue at start up"
date: 2010-03-08
forum: Hardware
---

### Post by MasterKush010 on 2010-03-08
Hi,

First off id like to say I'm an EX-MS fan boy for many years. The life change is purely an ethical choice for me in these crazy times. Thank you for this amazing OS and please keep up the good work! screw the corporate duality nightmare of mac & windows may they both lose numbers and a shimmering golden Ubuntu phoenix rise like Godzilla to smash them both in the new millennium! :D

Now, My issue.....

I have.. 780i evga mobo, Q6600 cpu, 4GB Good Ram (forget what now?),
WD 150GB Raptor as master drive, and 1TB WD10eads-00m2b0 HDD as slave.

Ubuntu 9.10, I use storage device manager to auto mount, but the issue was there before.

The Slave drive is 100% healthy (tested for 6 months in windows) and still works 100% even tested under windows vista. the drive is currently formatted to ext3, the issue is it doesn't always show up on start-up. Sometimes Its there, and sometimes its not, and sometimes even when the drive shows up half the files don't. That was scary the first time! 
The system sometime beeps loads as it shuts down and this seems to indicate the next time the PC is started the drive wont appear. I then restart a couple of time to bring drive back, if that font work I use recovery restart and that normally brings the drive back. Until the next time I reboot then we start the game again. Please help save me from this nightmare Déjà vu.

I have searched for an answer and solution and put in a good load of hours, I even formatted the drive to ext3 to try resolve the issue but I think now... I need the help of the U-TEAM! 

Sorry if I forgot crucial info please ask if you need anything.

Yours faithfully, 

Kush.

---

### Post by MasterKush010 on 2010-03-10
anyone...?

---

### Post by Fafler on 2010-03-10
Is the drive detected by the kernel, even if it doesn't show up in the file manager?```
sudo sfdisk -l
```What about adding to drive to /etc/fstab? This way the boot scripts will take care of it.

---

### Post by MasterKush010 on 2010-03-11
Yes, it's drive detected by the kernel, even if it doesn't show up in the file manager.

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   9127-   9128-  73316352    7  HPFS/NTFS
/dev/sda2       9128   18240    9113   73200172+  83  Linux
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

This is my /etc/fstab

/ ext4               defaults 0 0 
/media/SaveDisk ext3 defaults 0 0


Thanks for the help

---

### Post by MasterKush010 on 2010-03-11
wait.... this is with the drive mounted.

Disk /dev/sda: 18241 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start End #cyls #blocks Id System
/dev/sda1 * 0+ 9127- 9128- 73316352 7 HPFS/NTFS
/dev/sda2 9128 18240 9113 73200172+ 83 Linux
/dev/sda3 0 - 0 0 0 Empty
/dev/sda4 0 - 0 0 0 Empty

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start End #cyls #blocks Id System
/dev/sdb1 0+ 121601- 121601- 976759808 7 HPFS/NTFS
/dev/sdb2 0 - 0 0 0 Empty
/dev/sdb3 0 - 0 0 0 Empty
/dev/sdb4 0 - 0 0 0 Empty

So no, it isn't detected by the kernel when it doesn't show up in the file manager.

---

### Post by warfacegod on 2010-03-11
Have you tested it in Ubuntu? You can use System> Admin.> Disk Utility. Be warned though, it has a tendency to throw false positives. I prefer gsmartcontrol. If you would like to try that one, go to:

Application> Accessories> Terminal and type:

```
sudo apt-get install gsmartcontrol
```

Another thing to check is the owner of the drive. Right click the icon for the drive (when it's mounted) select properties> Permissions tab. If the owner isn't you (root isn't you) and you don't have any OS files on it or it's not your Home folder then it should be safe to change the ownership to you. That might help with getting it to mount on startup.

Again in Terminal:

```
sudo chown -R username:usergroup /media/drivename
```

Change username/group to the name you use to login to your computer and change drivename to what the drive is listed as in the media folder. In my case:

```
sudo chown -R warfacegod:warfacegod /media/8ea1854b-da0d-4dda-93cb-5996cfb0d6c8
```

---

### Post by MasterKush010 on 2010-03-11
Yes I have tested in ubuntu. I came back as fine.
Tried to install gsmartcontrol but gets to a page in terminal that asks me to set my mail sever with no options...? em,,,

Ran both the other codes you posted with my details. both ran without errors but not much changed? what was to happen?

Under permissions tab for the drive: "SaveDisk_" cold not be determined.

Cheers for super quick response.....

---

### Post by MasterKush010 on 2010-03-11
Got gsmart installed via synaptic. 

Lots of error msgs even when mounted.....

Device open failed, or device did not return an IDENTIFY DEVICE structure.

Smartctl: Device Read Identity Failed (not an ATA/ATAPI device)

Short INQUIRY response, skip product id

...any thing you need me to post from gsmartcontrol?

---

### Post by warfacegod on 2010-03-11
> **MasterKush010 said:**
> Yes I have tested in ubuntu. I came back as fine.
Tried to install gsmartcontrol but gets to a page in terminal that asks me to set my mail sever with no options...? em,,,

Ran both the other codes you posted with my details. both ran without errors but not much changed? what was to happen?

Under permissions tab for the drive: "SaveDisk_" cold not be determined.

Cheers for super quick response.....

I just tell Gsmart to install with no config for mail server. Did you check permissions after trying the "chown" code with the info I said to replace? What it should have done (assuming everything was in order) was change the drive owner to you.

The very last code, the one with warface and all that, is just an example. I put it there to give you an idea of what you should be putting into the Terminal. It won't actually do anything for you.

---

### Post by warfacegod on 2010-03-11
> **MasterKush010 said:**
> Got gsmart installed via synaptic. 

Lots of error msgs even when mounted.....

Device open failed, or device did not return an IDENTIFY DEVICE structure.

Smartctl: Device Read Identity Failed (not an ATA/ATAPI device)

Short INQUIRY response, skip product id

...any thing you need me to post from gsmartcontrol?

It's been a while since I've used it. Have you run an extensive test or what ever it's called?

---

### Post by MasterKush010 on 2010-03-11
Been working on it all evening .. The Drive failed! It was screwing around, fine one min. gone the next ..... Sorry for the confusion.

Thanks for a super pro service .... [SOLVED]

---

### Post by warfacegod on 2010-03-11
Glad to help.

FYI: Typing solved into a reply doesn't quite cut it.:p You'll have to "Mark as Solved" under Thread Tools. It should be about 2/3 the way up the screen on the right. Took me three months to realize that it was even there. Sorry about your drive hoss.

---

