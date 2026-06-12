---
title: "Nvidia graphics card drivers giving me trouble"
date: 2010-01-06
forum: Hardware
---

### Post by TBBucs on 2010-01-06
I downloaded and installed the latest Nvidia drivers, and when I rebooted, some strange things happened.  I was able to actually see the GUI, but it was incredibly slow to respond, and certain things weren't clickable. I launched the terminal and was able to see it, but I couldn't see a prompt, nor could I see anything that I typed (but typing something like gedit test.txt did brought up an empty file in gedit, so the keyboard is working).

The weird thing is that I've used these drivers before on a previous Ubuntu 9.10 installation.  I formatted the partition, added a separate /home partition, then reinstalled Ubuntu (same version), and now the graphics drivers are causing trouble.  I tried to go into xorg.conf and change the driver from "nvidia" to the generic "nv", but I can't get that far without things locking up.

Any ideas why it's not working this time around?  How should I proceed?

---

### Post by TBBucs on 2010-01-06
Bump.

---

### Post by Dr Belka on 2010-01-06
yeah, that always happens to me whenever I try to install nvidia drivers from their website.  I'm not good enough to recover from that so I generally have to re-install

---

### Post by LinuxRules1 on 2010-01-06
have you tried editing the xorg.conf file in the recovery console?

---

### Post by tekkidd on 2010-01-06
1. Are you sure you are using the correct drivers 

2. Boot into recovery mode and drop to a root prompt and reinstall the drivers

---

### Post by Ergo on 2010-01-06
I am having the same problems.  Everyone tells me I am not using the correct driver, but I have tried 3 different ways to install 3 different drivers.  It always turns out the same. My max resolution is 480x320.  If I push the issue with the computer, I eventually get only a blinking cursor at the command line, and a non responsive computer.  I can care less about 3-D acceleration.  I simply want the driver used when installing the system so that it will display 1024x768.  I do _not_ want to use the Nvidia provided driver.  They trash my machine's resolution _every_ time.  Can someone please give me a clue how to use just plain drivers that are only 2-D capable, so that I can see my Desktop again.  Editing xorg.conf did not help!

signed,

confusedAndFrustrated

---

### Post by Ergo on 2010-01-14
Because xorg.conf is no longer used by 9.10, the only resort was to change monitors to one the system recognized.  Changing monitors fixed the problem.  I also found that adding a xorg.conf would trick the system into using that file, but under the Monitor section, I had to add the monitors information by hand.  Adding the resolution I needed helped with this problem.  It was not a graphics card driver issue.

---

### Post by Ergo on 2010-03-14
I have also found that deleting all the hidden files in my home directory (that dealt with video) would reset my video settings.  Delete them, log out and log back in again and presto...you have a higher resolution and you can reconfigure your video settings.  Before I learned this, I had completely reinstalled my system with the exception of a /home directory which was unchanged.  After the new system booted I found that I still had the same problem.  I knew then that the problem had to be a hidden file in the home directory!

---

