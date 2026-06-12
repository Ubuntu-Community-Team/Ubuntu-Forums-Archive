---
title: "Help Please!  Ubuntu 8.04 Install Error"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by carbiznh on 2008-12-21
Hi everyone.  Thank you for taking the time to read this post. I am new to Linux and am trying to install Ubuntu from a install/live cd... I am having an error message on step 4 (maybe 5)..when it tries to start the partition phase of install this message comes up:

"No Root File Defined.  Please Correct In The Partitioning Menu"

I have not other options other than to exit installation....

My computer: 

XP PRO sp3
AMD 4800 Athlon X2 2.5GHz
250GB Hard Drive 
2GB Ram 

Please help......I am so tired of Windows...and was looking forward to a test drive on Ubuntu tonight.

Thanks,

David

---

### Post by Pumalite on 2008-12-21
[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

---

### Post by nlz on 2008-12-21
why don't you choose the guided install? then everything will go smooth.. Only choose manual install if you want to dual boot or have a seperate /home partition. If you don't understand the last sentence, you want to do the guided install..

---

### Post by carbiznh on 2008-12-21
Thanks Nlz...I do want to dual boot...still won't mount my hard drive for some reason..that error pops up...over and over again???

---

### Post by Pumalite on 2008-12-21
If dualbooting with Vista; allocate space for Ubuntu with the Vista partitioner first.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by carbiznh on 2008-12-21
pumalite...thanks for your assistance..I am running XP pro...is there a partitioning program in XP?

---

### Post by ranch hand on 2008-12-21
XP should have fdisk.  I don't know for sure, never ran XP.

---

### Post by markbuntu on 2008-12-21
You did not choose a mount point for  Ubuntu in the new partition, that is why you get that error. What you need to do is make your new partition root by choosing / as the mount point in the partitioner.

You do not need an XP partitioner to do this.

---

### Post by carbiznh on 2008-12-21
thanks...how do I choose / as the new mount point...I get through the language and keyboard set up and then it doesn't let me go any further...am I missing a step??

---

### Post by Pumalite on 2008-12-21
Burn a new CD. Do md5sum on the iso. Burn at 4x or less. Do not use CD-RW.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by caljohnsmith on 2008-12-21
Maybe this tutorial will help you get through your install OK:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

Let me know if that helps.

---

### Post by carbiznh on 2008-12-23
Thanks! I will try it.

---

