---
title: "How do I prevent hard drive from clicking?"
date: 2011-06-30
forum: Hardware
---

### Post by tmwdsi on 2011-06-30
I have an Acer Aspire 5736Z laptop running on Ubuntu 10.10 64-bit version. It has a Western Digital hard drive, but I do not know the exact model of it.

When running on battery power, the hard drive clicks every 5 - 10 seconds. It does not do this if plugged in, and I have no idea why. It only does this in Ubuntu (and I use the term "only" loosely, as it's the only Linux distro I have ran off the hard drive), and does not do it in Windows.

I feel as though this may have something to do with power saving.

How can I prevent the hard drive from clicking?

Thanks in advance!

---

### Post by wolfen69 on 2011-06-30
> **tmwdsi said:**
> 
I feel as though this may have something to do with power saving.


Most likely. Just go to power settings and check what's there.

---

### Post by JC Cheloven on 2011-06-30
Yep, laptops use to park often the disk heads to save battery and prevent the effects or rude movements. But discs are designed for a life of 600000 parks. Less than 15 parks / hour should be fine. 

To see what is the state of your disk, please install smartmoontools from the repos.  ```
smartctl -a /dev/sda
``` &#8594; gives you all the info.

Look at Power-on-hours (hours the disck has been running, and Load-cycle-count (times the head has been parked). THe ratio should be <15 aprox (incremental).

```
hdparm -B 254 /dev/sda
``` &#8594;  disables the head parking. In some systems it's 255. In this state the disk is exposed to the effects of shaking the laptop, so be specially careful. Also the disk will heat up more. You should check out its temperature often at the beginning ("smartctl -a" will tell you).

All the above is NOT persistent. To make it persistent you should make a .sh script and save it to some places at /etc/acpi/. You can find more details [here]("http://ubuntuforums.org/showpost.php?p=5031046&postcount=3")  

Hope this helps

---

### Post by Toz on 2011-06-30
When you unplug the laptop, the scripts in /usr/lib/pm-utils/power.d are run. One of those scripts sets the power management feature, and in the case of my WD hard drive, makes it click (head parking for safety purposes). I've only noticed this clicking on WD hard drives. On my 11.04 install, the file that controls this is **/usr/lib/pm-utils/power.d/95hdparm-apm**. To cancel out the effects of this file, you need to create an empty file with the same name in **/etc/pm/power.d/**. So basically (if the original file is /usr/lib/pm-utils/power.d/95hdparm-apm),
```
sudo touch /etc/pm/power.d/95hdparm-apm
```

Sorry, I don't have a 10.10 install to verify the filename.

---

### Post by tmwdsi on 2011-07-01
I think I fixed it. I created a script that contained this ```
sudo hdparm -B 255 /dev/sda
``` and saved it as "hd-fix" in my home folder, then I set it as a startup command. Haven't heard clicking since.

---

