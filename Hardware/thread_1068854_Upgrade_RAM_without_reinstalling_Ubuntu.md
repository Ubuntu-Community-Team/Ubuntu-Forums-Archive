---
title: "Upgrade RAM without reinstalling Ubuntu"
date: 2009-02-13
forum: Hardware
---

### Post by CanasClone on 2009-02-13
I just bought 4 gigs of RAM for my Toshiba Satellite and want to replace the current 1 gig I have installed. I understand I will have to change the partition structure to allow for a bigger swap partition which is risky but possible to keep your current OS installs. From there, I have no idea what in terms of OS software changes I need to do. My questions are this:

1. Once I've changed my swap partition size, how do I get Ubuntu to recognize the swap change and use the greater space?

2. Once I've installed the new RAM, how do I get Ubuntu to recognize the RAM change and use the greater space?

As the title suggests, I wish to not reinstall Ubuntu unless I have to. Thanks!

---

### Post by Yashiro on 2009-02-13
Just plugin your new ram. The only real reason you would need to adjust your swap is if you have hibernation problems after the upgrade.

The easiest way to sort this all out without learning command line stuff is to install Gparted the gnome partition editor.

If you have only one HD and you are running Linux from it, you will have to use the Ubuntu LiveCD to mess around with partitions.

---

### Post by hrod beraht on 2009-02-13
You don't *have* to change your swap partition. Your amount of RAM is taken into account when a swap partition size is decided, but there is no reason that they need to match. In fact, many people with 4GB of RAM figure that it's enough where they don't even need a swap partition.

Bob

---

### Post by roshanjose on 2009-02-13
yes i quite agree to that..

your 4GB could handle all the load and would still not require the swap...

formally the system just requires some space for the swap partition...so you should retain it

---

### Post by scientistuk on 2009-02-13
Personally id just delete the Swap if you never use the Hibernation feature as theres no need for it, I myself have 4gig ram and dont have swap partition. 

ram is more or less plug and play if u can say that.

---

### Post by perlluver on 2009-02-13
Just for Information, Ubuntu won't recognize all 4GB without the 64 bit edition.  It will only recognize 3.5GB, but that is plenty of enough memory.

---

### Post by scientistuk on 2009-02-13
is it not 2 or 3 gig limit with non 64 bit tech ? I could b wrong

---

### Post by sdennie on 2009-02-13
You can get 4GB of RAM on a 32bit install of Ubuntu.  See: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by airtonix on 2009-02-13
And you can always create a swap file which delivers same the peformance as when using a swap partition.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

