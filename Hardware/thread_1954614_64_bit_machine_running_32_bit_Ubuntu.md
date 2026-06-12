---
title: "64 bit machine running 32 bit Ubuntu?"
date: 2012-04-08
forum: Hardware
---

### Post by Podger51 on 2012-04-08
I recently acquired a laptop that had a clean drive running Ubuntu.
I just realised that the machine is a 64 bit & Ubuntu is 32 bit.
My question is, can I change / overwrite or upgrade the 32 bit Ubuntu with a 64 bit version without losing my data?

Thanks in advance.

---

### Post by roelforg on 2012-04-08
> **Podger51 said:**
> I recently acquired a laptop that had a clean drive running Ubuntu.
I just realised that the machine is a 64 bit & Ubuntu is 32 bit.
My question is, can I change / overwrite or upgrade the 32 bit Ubuntu with a 64 bit version without losing my data?

Thanks in advance.

I don't really see a reason to change.
Ubuntu defaults to pae install so there aren't really any benefits.
Besides, 32bit has more packages available.

EDIT:
I looked it up, turns out that default pae/non-pae is build specific,
look here for info enabeling: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by 2F4U on 2012-04-08
You cannot upgrade from 32 to 64 bit, it would be a fresh installation. Question is why would you want to change from 32 to 64 bit?

---

### Post by ahallubuntu on 2012-04-08
There are a few reasons one would benefit from a 64 bit Ubuntu:

- ability to access more than 4GB of RAM.  Actually, 32 bit laptops can usually access a bit less than 4GB.  My Dell laptop physically has 4GB but I "see" only about 3.4GB of it in 32 bit Ubuntu (which is what I normally run).  If I boot up a 64 bit Ubuntu CD, I can see 3.8GB of it (some is still reserved for integrated video).

- larger processes.  You are limited I think to 2GB for a process size on a 32 bit OS (some graphic and CAD utilities may have very large processes).  This is really not something the average person is ever going to worry about, though.

Neither of these is really a reason to wipe/re-install a 64 bit Ubuntu unless the laptop has physically more than 4GB.  If I had 8GB in my laptop, I'd want to see most of it.  I can live without a few hundred MB of it.

---

### Post by aura7 on 2012-04-08
I would recommend not to go for 64bit if you want to do some professional work with many third party apps. Third party apps are generally not available for 32 bit , otherwise for general use 64 bit is great.

---

### Post by Morbius1 on 2012-04-08
As stated above the pae kernel installs automatically so you will have access to more than 4GB of memory - just not all of it for the same process.

A 32 bit application can still only address 4GB but you can run multiple applications each accessing 4GB simultaneously. I have 16GB of RAM on my system and I use a 32bit OS. If I create a VBox guest it's limited to 4GB ( actually a little less ). But since I have the pae kernel I can create 3 VBox guests and run them all simultaneously.

---

