---
title: "Ubuntu shows no space"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by cjorg7 on 2009-10-18
Did a sided by side install of 9.04 and Vista.
When ubuntu boots I get two "can't set xfermode" error messages but os still starts.
When I try to perform updates, it says I have no space.
looks to me like Ubuntu partitioned about 2.3GB for OS and 176MB or so for Swap.
Any ideas?
Thanks in advance

---

### Post by cjorg7 on 2009-10-18
When using Liveboot cd ubuntu shows partitions.
Ubuntu as SDA/5, 2.3 GB and Swap as SDA/6 173MB

---

### Post by Yvan300 on 2009-10-18
Ok to fix your problem, just increase the partition size, oh and how big is your hard drive and how much free space is there on it?

---

### Post by cjorg7 on 2009-10-18
About 100GB free on Vista Partition, SDA2
Why would on install Ubuntu Only create a 2.3GB partition that appears no to be not large enough?

---

### Post by presence1960 on 2009-10-18
> **cjorg7 said:**
> About 100GB free on Vista Partition, SDA2
Why would on install Ubuntu Only create a 2.3GB partition that appears no to be not large enough?

did you use the slider in the attached pic to allocate how much space to give Ubuntu? If you did not then that is why.

---

### Post by cjorg7 on 2009-10-18
> **presence1960 said:**
> did you use the slider in the attached pic to allocate how much space to give Ubuntu? If you did not then that is why.
Thank you

---

### Post by presence1960 on 2009-10-18
> **cjorg7 said:**
> Thank you

You can probably fix this with gparted & Vista's disk management utility. Use Vista's disk management utility to shrink Vista. Then use gparted to add the freed up space to Ubuntu's partition. If you need help post back.

---

### Post by cjorg7 on 2009-10-21
Thanks. Sorry for the delay in the reply. I tried to shrink the Vista partition but it appears I can't make it any smaller without moving the page file.
I didn't have time recently so will try it next time I can.
is gparted installed with the default Ubuntu install?
Is the partition problem also causing the Xfermode errors I'm receiving?
I see you're in Philly, I'm fairly close actually.
Thanks,
Carl

---

### Post by Mark Phelps on 2009-10-21
> **cjorg7 said:**
> Did a sided by side install of 9.04 and Vista.

Sometimes, "side-by-side" is the term folks use to describe installing Ubuntu using Wubi -- inside Windows, and in that case, I believe the default space allocation is about 2.5GB.

If that's what you did, you need to use a different method to increase your Ubuntu space allocation, as shown in the Wubi guide linked below:

[https://wiki.ubuntu.com/WubiGuide%C2%A0]("https://wiki.ubuntu.com/WubiGuide%C2%A0")

---

### Post by cjorg7 on 2009-10-21
> **Mark Phelps said:**
> Sometimes, "side-by-side" is the term folks use to describe installing Ubuntu using Wubi -- inside Windows, and in that case, I believe the default space allocation is about 2.5GB.
 
If that's what you did, you need to use a different method to increase your Ubuntu space allocation, as shown in the Wubi guide linked below:
 
[https://wiki.ubuntu.com/WubiGuide%C2%A0](https://wiki.ubuntu.com/WubiGuide%C2%A0)
 
 I did not use Wubi. I installed it from the installer in the 9.04 download.
Are there any drawbacks to installing Ubuntu using Wubi?

---

### Post by Mark Phelps on 2009-10-21
> **cjorg7 said:**
> I did not use Wubi. I installed it from the installer in the 9.04 download.
Are there any drawbacks to installing Ubuntu using Wubi?

The primary one is that if the Window OS gets corrupted, you most likely lose access to Ubuntu because you're using the Windows loader to select the OS.

I've also heard that it runs slower, but I've not been able to confirm that myself.

---

### Post by presence1960 on 2009-10-21
> **cjorg7 said:**
> I did not use Wubi. I installed it from the installer in the 9.04 download.
Are there any drawbacks to installing Ubuntu using Wubi?

Yes, it is not made to be a permanent solution, it is a trial for those who are unwilling to partition their disk(s) until they decide they like Ubuntu.

Wubi is installed in the windows filesystem and as such is affected by windows filesystem fragmentation in the form of performance degradation.

Here are some links about wubi:

[http://en.wikipedia.org/wiki/Wubi_(installer)](http://en.wikipedia.org/wiki/Wubi_(installer))

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

