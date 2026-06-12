---
title: "how do I move /home to a new partition?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by sailthesea on 2009-10-22
HI guys I was wondering how to best do this:
 I want to create a new partition on laptops HDD and move my home directory there so I can install Mint as my primary OS for a little while, I have backups but would prefer to just duplicate the folder before I install
 I will be deleting Win 2000 totally and Jaunty(Wubi) for now but would like to move back to Ubuntu with a lighter distro for this machine Maybe as dual boot
 I have  various LiveCDs of Hardy Intrepid Jaunty and Mint for the best option of partition manager
 Many thanks for any help:)

---

### Post by cilynx on 2009-10-23
If you boot the Ubuntu Live CD (newer the better), you can use gParted to resize your current setup and make a new partition in the empty space you create.  Format the new partition with ext3 (or whatever your filesystem of choice may be)

Once that's done, mount up both the new partition and the old system so that you can see them both as folders on the Live CD Desktop.  From there, you can copy the files from your old /home to the new partition.

---

### Post by sailthesea on 2009-11-05
Thanks

---

### Post by michy99 on 2009-11-05
Here's a good walk-through:

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by jimbo99 on 2009-11-05
I was about to say that the first guy's description was only 7/8ths complete.  He didn't tell you how to set up the OS to use the new partition as your home by default.

---

### Post by oldsoundguy on 2009-11-05
The Psychocats tutorial is the one.

But would like to point out that changing the partition size does not work on all iterations of Ubuntu (for sure) and might not work on other builds.  YMMV, but I could not shrink the partitions on Mint and Myth comes right out and tells you at install that W.Y.S.I.W.Y.G. as far as their version is concerned.  NO separate partitions for the /home file!

So in those cases, you have to upgrade by doing a clean install .. using the old fashioned method of saving all your data (which you should do any way) and saving the /home file and anything from your eMail clent and all of your browser settings. (you still will lose your browser plug ins and have to re-install those!)

How do he know? ... just did it.

---

