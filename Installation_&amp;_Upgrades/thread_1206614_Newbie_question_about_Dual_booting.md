---
title: "Newbie question about Dual booting"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by lloux on 2009-07-07
I would like to dual boot windows XP and Ubuntu 9.04 on a HP media center 7170n. 

My question is if anything happens in the future and I would like to restore my PC to its original state (the way it was shipped) by using recovery CDs or hitting F12 at the startup, would that wipe my Ubuntu installation too?
Thanks

---

### Post by starcraft.man on 2009-07-07
Yes. That method usually relies on a hidden first partition (ENSURE you don't delete it at the partitioner) and will restore an image that was made either before it was shipped to you or after when you ran the imaging suite and it made DVDs for you. It can only restore what it was designed to, and I'm sure the OEM didn't intend for Linux to be on it (or likely care). It usually wipes all partitions and data not specified in the image and puts you back as you were when you made it. There are imagers available (like partimage) from linux, you could create your own image not reliant on their software and then delete the partition and images made from them. Google partimage and I'm sure you can find documentation.

If you want to avoid this problem and you have a second drive/external drive you may simply want to make a separate /home partition to store your data. That would allow you to use the images, and then you'd simply reinstall ubuntu and mount (but not format) the home partition. You might also do this with NAS, but I really think your home should be linked more physically to your main machine.

---

### Post by lloux on 2009-07-07
Thank you, I just wanted to make sure that I can reinstate my pc to its original condition before I proceed with Ubuntu installation.

---

