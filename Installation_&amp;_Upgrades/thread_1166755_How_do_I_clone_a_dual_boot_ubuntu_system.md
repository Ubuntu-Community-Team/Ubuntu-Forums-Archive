---
title: "How do I clone a dual boot ubuntu system???"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Nuticulus on 2009-05-22
Hi,

My laptop has a Vista partition and an Ubuntu partition. I have several applications that used to work on Vista, but I suspect that some trivial change might have caused them to stop working, so I want to restore the Vista installation using the provided disks. Will this affect (i.e. wipe) the partition with Ubuntu? Also, is there some way that I can make a custom liveCD that will install Ubuntu as I have set it up, if the Vista reset does mess things up?

Thanks in advance...

---

### Post by logos34 on 2009-05-22
> **Nuticulus said:**
> is there some way that I can make a custom liveCD that will install Ubuntu as I have set it up, if the Vista reset does mess things up?

There is something called [Remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") (cd/dvd)...You could also just make an backup image of ubuntu with Partimage on the ubuntu live cd, or using Clonezilla live cd/usb.

---

### Post by Nuticulus on 2009-05-23
I tried Remastersys but when I tried to run the LiveCD it froze with a hashed-up looking ubuntu logo on both sides of the screen. With Partimage, which partition do I save? The main one, the linux-swap, or both?

---

### Post by logos34 on 2009-05-23
> **Nuticulus said:**
> With Partimage, which partition do I save? The main one, the linux-swap, or both?

Just /, the system partition.

---

### Post by Nuticulus on 2009-05-23
Assuming the Vista reset deletes my Ubuntu partition, how should I go about reinstalling my Ubuntu image?

---

### Post by logos34 on 2009-05-23
just use the live cd to start up partimage, point it to the target partition and restore the image...its all explained in the documentation

---

