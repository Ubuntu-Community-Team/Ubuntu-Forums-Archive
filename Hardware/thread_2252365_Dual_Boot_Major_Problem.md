---
title: "Dual Boot Major Problem"
date: 2014-11-11
forum: Hardware
---

### Post by poscomp on 2014-11-11
Microsoft must have changed something. I've always done my dual boot by installing windows then installing Ubuntu and having Ubuntu split the drive. Now I tried to put a new drive on my system, so I installed the same Windows 7 Ultimate. The install went fine. I then went to install Ubuntu and when it came time to split the drive, that option was gone. I tried the install again and got the same results. So, I went back to Windows and shrunk the drive leaving enough for my swap drive and Ubuntu drive. Now it shows nothing on the drive so if I install, I will write over Windows. What did Microsoft do so that I can no longer see the MS partition? I took out an older drive with just Windows 7 on it and it worked fine. It's only with a new install using the same software. What can I do to dual boot the new drive?

---

### Post by coffeecat on 2014-11-11
I don't think that Microsoft has done anything. More likely that there is either:

1 - A partition table irregularity which Windows doesn't mind but which is confusing the Ubuntu installer.

2 - Residual RAID metadata on the new drive - which also confuses the installer. Of course, this is only relevant if the "new" drive was originally used in a RAID setup. 

So - is this a brand new drive, or is it one that has been used in a RAID array? If not, boot into the live desktop from your Ubuntu DVD/USB and post the output of this terminal command:

```
sudo fdisk -lu
```

Also - if you can get a screenshot of the open gparted window in the live session, that would be useful too.

---

### Post by hopper2 on 2014-11-11
If you have 2 hard drives I would just put Ubuntu on the other drive. It's better too because if Ubuntu screws Windows up (when it's on 1 drive), then everything's gone but if it's on 2 drives you'll be safe.

---

