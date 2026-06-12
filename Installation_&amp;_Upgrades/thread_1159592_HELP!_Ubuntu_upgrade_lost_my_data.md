---
title: "HELP! Ubuntu upgrade lost my data?"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by ttallos on 2009-05-14
I preformed an upgrade of my mirror array to ubuntu 9.04 I had 100Gig of data after rebooting the machine became unusable and just gave a command prompt. I then installed a fresh copy of ubuntu 8.10 and slaved one of the mirrored drives but it does not appear in computer. Can anybody out there help me to get back my data, or just be able to read either of the mirrored drives. I could put back the mirror the way it was if need be. Thanks for any help.

---

### Post by ttallos on 2009-05-14
I noticed the safe mode feature and I am running something like a scandisk feature and it says it is repairing inodes this may at least get it up and running so I can view the file system. If anyone out there has any ideas please let me know. Thanks

---

### Post by ttallos on 2009-05-17
I hope this helps someone out there. The way I fixed the problem was I started the array in safe mode then did a scan disk to fix any errors from the safe mode screen. After that I loaded ubuntu on a brand new hard drive and hooked back up the array as a secondary drive. poof all my data was able to be copied to the new drive using grsync. I am going to keep this configuration too!

---

