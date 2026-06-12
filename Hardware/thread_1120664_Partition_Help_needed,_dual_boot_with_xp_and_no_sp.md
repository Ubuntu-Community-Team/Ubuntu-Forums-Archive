---
title: "Partition Help needed, dual boot with xp and no space."
date: 2009-04-09
forum: Hardware
---

### Post by polkadotteapot on 2009-04-09
Hello,

I've had a good search (of course!) but couldn't find a particular solution to this:

I'm dual booting xp and ubuntu 8.10 on my acer aspire one 120gb hard drive and I'm a noob. I also don't have access to an optical drive at the moment.

I'm now running out of space due to my downloading of things and I want to run ubuntu most of the time and keep xp for the occasional laugh.

I used wubi to install and set aside 10gb for ubuntu. Gparted shows me my device dev/sda 149.05 gib has two partitions under dev/sda2. One FAT32 with 4.03gb used out of 4.88, and one ntfs with 41.96gb used out of 144.17gb.

I want to allocate most of the space to ubuntu so I can download larger files than I currently have space for, apparently. I keep all my guff on an external hard drive but it's taken me a couple of weeks to get everything working, installed properly and set up the way I want on ubuntu to I really don't want to loose that.

Any help would be most appreciated.

---

### Post by polkadotteapot on 2009-04-09
Basically I'm bumping and asking if I can just put a partition in to use on this os, is that doable without wiping everything? I don't really know about these things and all my scroogling hasn't helped much so far.

---

### Post by meierfra. on 2009-04-09
You can resize the  virtual disk used by Wubi with LVPM:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

(the instructions for resizing are close the end of the page)

But since you are now using Ubuntu as your main OS, you  might consider converting your Wubi installation to a regular Ubuntu installation. This can also be done with LVPM.

---

### Post by polkadotteapot on 2009-04-10
Thank you very much, that was just what I needed, even if I have proceeded to do my machine a diservice.

---

### Post by meierfra. on 2009-04-11
> even if I have proceeded to do my machine a diservice.
????????????????

---

