---
title: "Ubuntu Package and update managers fail to open"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by Tom11235 on 2009-07-14
Hi, I recently reinstalled ubuntu, version 9.04 onto and external hard drive. After reinstalling and starting up ubuntu for the first time I launched the update manager which downloaded and proceeded to install the updates. However, an error occurred with some of them (sorry, could not reproduce the specific error), and after trying to update again with no success I restarted my computer. After the restart I tried to update again, but to no avail. The notifications tab shows a stop sign, which displays the error, 

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'This usually means that your installed packages have unmet dependencies" 

when I hover my mouse over it. I tried the right-click menu along with suggestions from other posts on the forums: 'sudo apt-get update', 'sudo apt-get install', and 'sudo apt-get upgrade', but none enabled me to install the updates or remove the error message, even after restarts. 

This is the output for sudo apt-get install/upgrade:
Reading package lists... Done
Segmentation faulty tree... 50%

It can acquire updates easily via the "right-click menu" and the terminal, but cannot install them. I would appreciate any assistance in resolving this matter. Thanks in advance.

---

### Post by aesis05401 on 2009-07-14
Try this:
```

sudo dpkg --configure -a

```

This will attempt to reconfigure packages that have already been unpacked.  

Please post back with results.

---

### Post by Tom11235 on 2009-07-16
Thanks for the assistance and sorry for the delay; however, my PC failed to boot properly shortly after posting the thread due to conflicts between my installation of linux and my external hard drive. Consequently, I was forced to format and revert to a previous OS. I appreciate the help but will probably have to scrap this for now until I can get a stable installation on my external hdd.

---

