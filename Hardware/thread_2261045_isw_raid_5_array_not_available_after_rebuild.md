---
title: "isw raid 5 array not available after rebuild"
date: 2015-01-15
forum: Hardware
---

### Post by steven-w-higginbotham on 2015-01-15
I had been using a raid 5 array (three disks), mounted at /home/ and suffered a single drive failure, resulting in a degraded array. I've replaced the drive and selected the option in my BIOS to use the new drive as part of the RAID array. BIOS informed me that the array would be rebuilt in the OS. 

Unfortunately, I was not able to log into my user account when the computer had booted into ubuntu, and reinstalled ubuntu in order to be able to use the gparted GUI and web browser. (I've realized since reinstall that this may have been fixable by using a different boot option.)

I didn't know that the ISW raid controller was a 'fake raid' setup when I initially installed, and I am very novice at disk management, but have learned that this may be a complicating issue as compared with having ubuntu manage the RAID array. At any rate... the main problem is that my raid array seems healthy, but the files aren't present when I mount it to /home/ (only 'lost+found' shows up).

I'm not sure what outputs to provide to help illuminate the issue either... dmraid? mdadm? fdisk? gdisk? I'm lost. :(

---

