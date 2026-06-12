---
title: "Text screen replaces usplash loading bar and Ununtu logo"
date: 2008-09-08
forum: General Help
---

### Post by Animeniac on 2008-09-08
I have installed another Linux distro in my computer (PCLinux, to be exact), and this one formatted the swap partition in the installer. Whenever I format my linux swap partition when installing another Linux distro, I then get a text screen instead of the Ubuntu usplash, when I'm booting Ubuntu.

I tried using Startup Manager to fix it - I enabled boot splash and disabled text, and it didn't work. I even used QParted in my hard drive-installed Ubuntu to format the linux swap partition. I still don't get the usplash.

The only solution I know that worked is by re-installing Ubuntu. I don't want to re-install Ubuntu and install all the programs I want again (I have a /home partition, so all my personal files are saved). I'm sure there is another solution than re-installing Ubuntu. Is there? If there is, please show me one. Thanks.

---

### Post by dhimate on 2008-09-21
I am also facing the same issue. After formatting the swap partition, I see Ubuntu usplash and logo for some time and then it starts with boot text.

---

### Post by dhimate on 2008-09-21
I got this fixed. 

Please refer to [this]("http://ubuntuforums.org/showthread.php?t=746132") and [this]("https://bugs.launchpad.net/ubuntu/+bug/205990")


Hope this works for you as well. :popcorn:

---

### Post by anotherdisciple on 2008-09-23
Please make sure to mark your thread as SOLVED when you get everything fixed. Thanks.

---

### Post by swb on 2008-11-23
> **dhimate said:**
> I got this fixed. 

Please refer to [this]("http://ubuntuforums.org/showthread.php?t=746132") and [this]("https://bugs.launchpad.net/ubuntu/+bug/205990")


Hope this works for you as well. :popcorn:

I've also had this problem for a while, my uids were wrong, but even after fixing them it still drops out to text at reading files needed to boot. Any suggestions?

---

