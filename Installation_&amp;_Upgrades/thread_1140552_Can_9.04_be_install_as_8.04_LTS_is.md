---
title: "Can 9.04 be install as 8.04 LTS is??"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by RobertoJiron on 2009-04-27
Can one upgrade from 8.04 LTS to 9.04?

I am running a dual boot in my computer, I have vista and ubuntu 8.04 LTS.
I was running LTS from a CD Rom but I finelly disated to install LTS as a regular program in windows... You know how that goes.
My question is can 9.04 be install as 8.04 lts in my computer???

---

### Post by ptn107 on 2009-04-27
Your upgrade path is 8.04 LTS > 8.10 > 9.04.

---

### Post by lovinglinux on 2009-04-27
> **RobertoJiron said:**
> Can one upgrade from 8.04 LTS to 9.04? I am running a dual boot in my computer, I have vista and ubuntu 8.04 LTS.

As already explained, you need to upgrade to 8.10 first, then to 9.04. But, since you are running a dual-boot, you could move your personal files from the Ubuntu partition to the Windows partition, then make a clean install of 9.04 in the Ubuntu partition, then copy your personal files back to Ubuntu.

As long as you know how to partition stuff and don't erase Windows, this method will be less prone to errors then upgrading to 8.10 > 9.04.

If you have a separate partition for your home directory, then you could also keep your settings and there is no need to move your personal files to to Windows.

Recommended reading:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

> **RobertoJiron said:**
> I was running LTS from a CD Rom but I finelly disated to install LTS as a regular program in windows... You know how that goes.

Your current Ubuntu was installed with Wubi from Windows or did you actually installed Ubuntu on a new partition?

I'm asking this because is not very clear what you did and if you used Wubi, then I guess the method I described for installing fresh don't apply. I'm not sure if it would be possible to do a fresh install over a Wubi installation. But I guess the best method would be to uninstall the current Wubi installation and and installa new one using the 9.04 version.

> **RobertoJiron said:**
> My question is can 9.04 be install as 8.04 lts in my computer???

I don't understand the question.

---

### Post by Sef on 2009-04-27
**Back up** your **data** before upgrading or installing.   There are no 100% guranatees that all will go well.

---

### Post by RobertoJiron on 2009-04-27
Lovely!
I thank you for your help fellas.
Can't wait to do the new install.
Thanks a bunch!

---

