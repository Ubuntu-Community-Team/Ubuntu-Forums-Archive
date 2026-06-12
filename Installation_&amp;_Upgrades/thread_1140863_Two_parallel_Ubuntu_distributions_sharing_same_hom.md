---
title: "Two parallel Ubuntu distributions sharing same home"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by zuheyr on 2009-04-28
Hello,

I am using Ubuntu 8.10 desktop on my Dell Inspiron. I want to install 9.10 in such a way that they will both share the same existing home partition. 

I am using dual boot with Vista!

Could you please help me with that. Thanks for reading, regards
Zuheyr

---

### Post by VastOne on 2009-04-28
> **zuheyr said:**
> Hello,

I am using Ubuntu 8.10 desktop on my Dell Inspiron. I want to install 9.10 in such a way that they will both share the same existing home partition. 

I am using dual boot with Vista!

Could you please help me with that. Thanks for reading, regards
Zuheyr

Follow the instructions here: (smartest move I ever made)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck...

---

### Post by zuheyr on 2009-04-29
Thank you very much, I appreciated it. I will have to study.

Regards, Zuheyr

---

### Post by ksennin on 2009-05-01
If I am not mistaken, that page is about creating a separate partition for home so you can reinstall retaining the home data.  But if like the OP I want to have different ubuntu releases coexisting on a same pc, and sharing the same home partition (which I already installed as a separate disk partition, thus not needing the info in that linked page) will I have any troubles?  Will setting be shared properly?

---

### Post by zuheyr on 2009-05-01
Hello,

Thank you. I was just going to ask the same question after studying the linked page.

This is exactly what I want to do as well. I want to install the new Ubuntu on a different hard disk in the PC (I have plenty of space) and I want it to use the existing old home without copying anything. 

I think while it is installing, installer asks for creating mounting points. Spreading the systems over several hard disks will create any problems? 

Thank you for reading.

---

### Post by ksennin on 2009-05-01
Maybe someone can answer us.  

As to your last comments, I don't think it will create serious immediate problems to spread the components over various disks, but it could be a problem if one of the drives starts failing.  ALso, you would need to keep both drives spinning at the same during operations and it would be more energy-consuming.  Also, exchanging one drive for a larger one becomes problematic down the road.

What I do is keep all the system partitions in a single drive, and use a second drive for data storage.  

Presently I have my main 200GB drive divided into a WinXP partition, a / partition for ubuntu 8.10, a home partition, a swap partition, a small NTFS partition to share stuff between systems and keep downloads temporarily, and another partition to install new versions of ubuntu.

Then I have a 500GB drive for storing/sharing data, in a single NTFS partition, which I access only when looking for particular stuff.

I want to install Ubuntu 9.04 Jaunty on the spare partition of my main drive and share the home and swap partitions already existing.  But I do not know if the home sharing would be feasible operations-wise.

If it works I may also create a new partition and reinstall 7.10 Gutsy which was the version that worked best with my VIA unichrome integrated video.

---

