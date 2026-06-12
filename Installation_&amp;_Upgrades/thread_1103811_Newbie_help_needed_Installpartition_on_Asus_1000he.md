---
title: "Newbie help needed: Install/partition on Asus 1000he"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by Seattlite on 2009-03-23
I'm a complete Linux newbie, but very ready to convert. I've been reading everything I can find (online and magazines) for several weeks, but am completely stymied and stuck at the install point. Help?

I have a new Asus Eee PC 1000he, 160GB, pre-partitioned at factory to roughly 82GB and 63GB. Preinstalled with Windows XP, which I have to keep for my work. It appears that XP is on one partition (C:) and D: is empty. (I'm not exactly sure where the installed recovery is located.)

I have two different Intrepid Ibex (Ubuntu 8.10) installation disks purchased through magazines. Also two downloaded and burned disks of Eeebuntu, Standard and NBR. I *think* I want to go with Eeebuntu Standard (though am still wondering about regular Ubuntu and Kubuntu). At this point I just want to go with one and DO it, already! :/

Everything I've read tells me that the live CDs should offer one or more "Guided" partitioning options. But all I've seen so far with any of my disks is one "guided" option that will format my whole hard drive, or else a manual option. So, a few questions:

1) It seems like the live install CDs are not 'seeing' my XP installation. But how can I tell for sure? And why might they not be?

2) Why are my install CDs not giving me a Guided resize option?

3) If I'm stuck with only two options, "Guided - use entire disK" and "Manual", I need help to understand the manual process. Everything I've read says that "Manual" is only for intermediate to experienced users, but it's feeling like my only option after several weeks of trying (plus, while I'm very Linux green, I'm overall computer savy fairly far above the average home user). But then, see my next question.

4) What do the various partition designations mean? /dev/sda# etc to four? I don't know how large/small to make each when I have no idea how to tell what part each is related to. 

5) Should I install Ubuntu on the same existing parition as XP, and/or resize that partition, or else install it on the already existing separate partition? If I do that, I assume I should resize the XP partition (currently 82GB) to be smaller. I want to be able to file swap between XP and Ubuntu. I semi-understand that Ubuntu will require a couple of partitions (/home, /swap... I think). I'm still confused about sizes for everything. I've also read a little about ext32 but have NO idea how to format to that.

Help? Direction? Guidance? Tired of being stuck and want to move forward with an install!

---

### Post by Seattlite on 2009-03-24
bump...

---

### Post by microman777 on 2009-03-25
You can install Ubuntu directly from your Windows XP with Wupi. 

[http://wubi-installer.org/](http://wubi-installer.org/)

Thats probably the easiest way to do it IMO. Then you can dual boot to XP or Ubuntu as you learn Ubuntu.

You can install it in the C: Drive with Windows XP and later even uninstall it really easy with Wubi.

---

