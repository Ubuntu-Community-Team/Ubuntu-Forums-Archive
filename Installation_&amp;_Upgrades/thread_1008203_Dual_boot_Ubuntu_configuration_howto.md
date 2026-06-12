---
title: "Dual boot Ubuntu configuration howto?"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by i-o on 2008-12-11
Hi,
I couldn't find good answers with search for my problem.
The background: I need to have ubuntu 8.04 & 8.10 installed on same computer in dual-boot setup. I want those to be on their own encrypted partitions so that the configurations dont get mixed up. 
So what is the working order in getting this thing to work and how should/could the hd be partitioned?
THX in advance.
-io

---

### Post by caljohnsmith on 2008-12-11
I just wanted to mention that you don't necessarily have to encrypt their partitions in order to keep them separate; if you are careful to install 8.04 and 8.10 to different partitions, they won't touch each other. One of them will need to be in charge of Grub on start up though, and I would recommend using 8.10. If you would like a step-by-step guide of how to install Ubuntu, here's one you could check out:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html) 

It's up to you though if you want encrypted partitions or not; good luck and let me know how it goes.

---

### Post by i-o on 2008-12-12
Well, the disk encryption is not what I want to do. It's more like what I have to do due to company policy of laptop hdd's.
Anyway my problem is more specific. I have 8.04 installed ok and the disk partition before 8.10 installtion looks like:
-Small / Primary /ext3 / boot partition
-Large / Logical / Physical volume for encryption
  *-Physical volume for LVM / Encrypted volume
    **-Small swap
    **-Larger data partition

For 8.10 I created an another 'Logical / Physical volume for encryption' which looks like the one already existing for 8.04.
On 8.10 installation however cannot install LILO boot loader on HDD. The options where it offers it to be installed are;
- /dev/mapper: Master Boot Record
- /dev7mapper/sda6_crypt: new Ubuntu partition
- Other choice (Advanced)
Therefore this step is skipped and no boot loader is istalled which of course means that 8.10 installation cannot be accessed.

So I quess the partitioning must be done on some other way. But how?

---

### Post by i-o on 2008-12-18
Anyone?

---

### Post by philetus on 2008-12-18
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.linuxquestions.org/questions/linux-general-1/dual-boot-two-linux-distros-564582/](http://www.linuxquestions.org/questions/linux-general-1/dual-boot-two-linux-distros-564582/)

---

