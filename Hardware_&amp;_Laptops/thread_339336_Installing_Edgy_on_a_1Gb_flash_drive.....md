---
title: "Installing Edgy on a 1Gb flash drive....?"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by Martin A on 2007-01-15
Evening folks,

I recently purchased a HP Pavilion dv2000 (AMD Turion64 X2 1.8GHz, 2Gb RAM, 120Gb HDD), and I need to keep Windows on the hard drive (there is a tedios, longwinded explanation as to why i can't install it on the main drive that I'd rather not go into), and I would like to know how (if?) I can install Ubuntu to a 1Gb USB flash drive. The computer is certainly capable of booting from a flash drive as I had DSL running OK from one..  

Thanks in advance!

Martin

---

### Post by bedlam on 2007-01-18
It's not the answer you want, but I too wanted to keep my windows installation intact.
I bought another laptop hard drive and swapped them over. simple to do, with a fresh install and best of both worlds.

---

### Post by antar on 2007-01-18
1GB might be a bit too small. The installer reccomends at least two. And keep in mind, you're going to need at least 256MB for your swap.

---

### Post by vyruss on 2007-01-18
> **Martin A said:**
> Evening folks,

I recently purchased a HP Pavilion dv2000 (AMD Turion64 X2 1.8GHz, 2Gb RAM, 120Gb HDD), and I need to keep Windows on the hard drive (there is a tedios, longwinded explanation as to why i can't install it on the main drive that I'd rather not go into), and I would like to know how (if?) I can install Ubuntu to a 1Gb USB flash drive. The computer is certainly capable of booting from a flash drive as I had DSL running OK from one..  

I did this, this howto worked perfectly for me. I also have about 300 mb free on the stick!
Just be aware that USB sticks are VERY slow, compared to a hard drive.

HOWTO: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by ganiawg on 2007-01-19
I have a 5 year old 2GB hard drive sitting at home. When I tried to install Ubuntu 6.10 to my 2GB hard drive using the live CD, it did not work. It looks like you need to have at least 2.5-3GB Hard drive, including the partition for Ubuntu and swap.

---

### Post by vyruss on 2007-01-21
> **ganiawg said:**
> I have a 5 year old 2GB hard drive sitting at home. When I tried to install Ubuntu 6.10 to my 2GB hard drive using the live CD, it did not work. It looks like you need to have at least 2.5-3GB Hard drive, including the partition for Ubuntu and swap.

I repeat, to the OP: you do not have to actually INSTALL onto your USB Stick, you can follow the HOWTO linked on my previous post and make a 1 GB stick work as a fully READ-WRITE live CD!

However: it would be best that you allocate some swap space on a hard disk.

---

