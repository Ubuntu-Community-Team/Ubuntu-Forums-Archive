---
title: "2nd Hard Drive as /home/"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by n8oay on 2007-03-13
I have been dual booting my Linux computer with 3 different distros while trying to decide which I like best, and have decided to stick with Ubuntu. The task at hand now is to use the 2nd drive (actually hda) with Ubuntu for /home/, and the boot drive (hdb) for OS and programs. What do I need to do to have the 2nd drive show up under /home/ ?

---

### Post by russell.h on 2007-03-13
If you are doing a fresh install of Ubuntu when you get to the partitioning part set /home as the mount point of hda, and / as the mount point of your other hard drive. Worked for me anyway.

If you're not doing a fresh install check out [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by n8oay on 2007-03-14
Thank you! I need to spend some time reading that psychocats web page - lot's of good stuff there!


> **russell.h said:**
> If you are doing a fresh install of Ubuntu when you get to the partitioning part set /home as the mount point of hda, and / as the mount point of your other hard drive. Worked for me anyway.

If you're not doing a fresh install check out [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by n8oay on 2007-03-14
This Linux Rookie needs help! :confused:  I have the drive formatted (ReiserFS), but I am having problems converting the code on [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) to fit my situation. The partition to be mounted as the new '/home' is /dev/hda1 and the current '/home' is on /dev/hdb. When I try to make a directory, I get an error message that the folder does not exist.

I could take the easy way out and do a clean reload, but I won't learn anything doing that...and I have watched various distros install a couple dozen times while trying to decide which I wanted to use.



> **russell.h said:**
> If you are doing a fresh install of Ubuntu when you get to the partitioning part set /home as the mount point of hda, and / as the mount point of your other hard drive. Worked for me anyway.

If you're not doing a fresh install check out [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by n8oay on 2007-03-18
I am still having trouble with this. I tried again going through the steps documented on [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) this time copying and pasting each command from the web page and changing the commands where necessary (/home is currently on hdb1, and I want to move it to hda1), and it still is not working. When I reboot, I do not have access to /dev/hda1 getting a message that I do not have permission to use it. Also, I do not see any of the directories that were made during the process. It seems to me like the changes are not being saved when I reboot. While I am in the Terminal when booted to the Ubuntu DVD, I can cd to the /old and /new directories that I am making. I have done this several times, and keep coming up with the same result.

---

