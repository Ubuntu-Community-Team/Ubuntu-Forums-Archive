---
title: "Solution: Laptop Freezes, no keyboard access, forced to hard-power off"
date: 2008-12-24
forum: Hardware
---

### Post by krlhc8 on 2008-12-24
If you have a 3-year old laptop with a Intel Core Duo processor like I do, and your: 

system has been freezing, you can't use your keyboard to safely restart, it hangs even before getting to GRUB in the boot process, you know it can't be your harddrive like someone might suggest since you just got a new one!!!, and very importantly that upon restart your BIOS system-check output informs you that it only detects 1 of your 2 processor cores!

then be thankful you have Linux because this problem has a workaround (at least it worked for me).  What's happening is one of your cores of your processor is going bad.  Luckily you have two, right!  What I did to solve this problem is to use a Linux command to disable the bad core of my processor, which for me was the second core CPU1 (the first being CPU0).  This fix should buy you enough time to get a new laptop (trust me, you'll want one soon because battery life sucks with only one cpu).

The following is a Linux command to disable the secondary core, CPU1.  Upon startup of your computer, race to a terminal and enter the command.  
Afterward, you should hopefully notice that the computer is no longer acting wonky and is not freezing or anything.  If it didn't work, then maybe 
your other core is bad, so exchange .../cpu/cpu1/... for .../cpu/cpu0/...

```
echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online
```
Don't put sudo in front of the command, it already has it inside.

If the command actually fixes your issue, then congradulations!  Now let's get this badboy automatically running on startup.

First, create a shell script called disablecore.sh in init.d:
```
sudo gedit /etc/init.d/disablecore.sh
```

Second, paste the code, save and exit the text editor:
```

#!/bin/bash
### INFO START
# A Script to Disable CPU1
### INFO END

echo 0 | tee /sys/devices/system/cpu/cpu1/online

```

Finally, you must run this command in the terminal so that the script in init.d is run in the appropriate run levels (2 3 4 5) and is started and stopped with a sensible priority (in this command 01 means disablecore.sh is the first script started when booting up and 99 means it's the last script stopped when shutting down).
```
sudo update-rc.d disablecore.sh start 01 2 3 4 5 . stop 99 0 1 6 .
```

That's it!  I hope this helps someone.

---

