---
title: "Dell Inspiron 7559 on Ubuntu 17.10"
date: 2018-03-03
forum: Hardware
---

### Post by BuntuDolphin on 2018-03-03
):P I just wanted to post this in case someone else has the same experience, and is frustrated that they can't get their computer to work under Ubuntu. (I have the older model with an i5 Skylake processor) 
What worked for me on this computer is nomodeset kernel parameter on install, then install nvidia proprietary drivers, Fast boot and secure boot turned off (FN & F3 to turn off fast boot, it's not in the settings for some odd reason), intel speedstep turned off, and install intel-microcode from the repositories for the Skylake processor. 
Make SURE you turn off Fast Boot. I didn't, and was wrestling for hours trying to figure out why I couldn't get to the boot menu. #-o  
Well that's all, just wanted to help someone out.

---

### Post by mörgæs on 2018-03-04
Thanks for posting.
If you add to the [compatibility thread]("https://ubuntuforums.org/showthread.php?t=1543006") there is a better chance that people will see your advice.

---

