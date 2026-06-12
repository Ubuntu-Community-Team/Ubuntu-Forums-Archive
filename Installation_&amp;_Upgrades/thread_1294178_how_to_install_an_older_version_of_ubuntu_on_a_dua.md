---
title: "how to install an older version of ubuntu on a dual boot machine"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by mefistofeles666 on 2009-10-18
Hello all,

So I installed intrepid today on a new computer and intrepid wasn't detecting the internet. Somehow I managed to delete the network manager, and I was thinking of re-installing intrepid. But I decided it would be best if I just install hardy. So I was wondering if it's possible to install hardy and erase intrepid at the same time?

If not, how do I re-install intrepid from an iso in an usb drive?


thanks so much 
ps. I'm using vista

---

### Post by carnagex420x on 2009-10-18
Either way you would be doing a new install. The easiest way to do that would be to use "Unetbootin" to make a bootable USB for the install. You just need to settle on a Hardy or Intrepid iso.
I still use Intrepid and love it. Long live 8.10!

---

### Post by Lars Noodén on 2009-10-18
Yes, it is possible to install hardy and erase intrepid at the same time.  Just make sure that the system partitions used by hardy are the ones that intrepid was using.  

If you don't already have a separate /home partition, when you get  a chance, repartition the hard disk so that you have one.  Makes it easier to switch versions or try newer distros or different distros while leaving the main one alone.

---

### Post by mefistofeles666 on 2009-10-18
So, if I was to start installing hardy it would simply install over intrepid in the partition I have for linux? that's my main concern right now, I don't know if its possible to simply start installing hardy or if I have to delete intrepid first.

---

### Post by carnagex420x on 2009-10-18
When you go through the install process you have to 1)select a disk and 2)select your partitioning scheme. This is the point where you can delete and format you old partitions, and install to the new ones at the same time.

---

