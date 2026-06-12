---
title: "Power Outages Destroy (and I mean Destroy!) Installation"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by promet on 2005-11-27
Hello,

I live in an old victorian flat. Unfortunately the eletrical system is as old and victorian as the flat itself, also the landlord is making all sorts of remodels and whatnot. Consequently, I am more prone to abrupt power outages than your average Ubuntu-nite.

I am planning on buying a nice reliable uniterruptable power supply, but money is tight at the moment. So in the meantime I thought I would appeal to you good folks.

recently, during a bout of outatges, I had come home to find my 5.04 Hoary install in various stages of crucial destruction. It seemed to have survived okay before, but now seems annihilated after "cold" power offs. I have since upgraded to Breezy 5.10 in hopes of better results but haven't had an outage since then.

As I understand it, this is likely due to Ubuntu's inability to cleanly unmount filesystems and services. It scrambles the filesystem and makes for a horrific boot process, and indeed sometimes scrambles GRUB for an inability to boot at all.

So I was wondering, is there any software precaution possible to soften this sort of blow ( it WILL happen again ) and I always am of the mind to reinstall rather than get out the toolbox on a deeply corrupted system.

So if anyone has any suggestions (Other than creating a GRUB boot disk, which I've done) until I can scrape together the gelt for a UPS. I would be eternally grateful. And thanks.

Signed,
UBUNTU in the dark :???:

---

### Post by lcg on 2005-11-27
[QUOTE=promet]
So I was wondering, is there any software precaution possible to soften this sort of blow ( it WILL happen again ) and I always am of the mind to reinstall rather than get out the toolbox on a deeply corrupted system.

So if anyone has any suggestions (Other than creating a GRUB boot disk, which I've done) until I can scrape together the gelt for a UPS. I would be eternally grateful. And thanks.[/QUOTE]
First of all, you should choose a journaling filesystem like ext3 or reiserfs. That should be a first step towards having consistent filesystems.
Second, I like to put /boot on a separate partition which is not mounted during normal operation (via the option noauto in the fstab). That way, if your system goes down, the kernels are safe and when you restart, there will at least be a kernel there to boot and to fsck from. (However that means that you have to manually mount /boot before you can e.g. update your kernel or change the grub configuration.)

Other than that, praying might be an option. ;)

HTH,
Lars

---

### Post by promet on 2005-11-27
After rooting around a little I found another thread about system backups. I think that Mondo Rescue (mondoarchive) will provide a tidy solution. Check it out if you're looking for backup-restore solutions:

[http://ccp14.minerals.csiro.au/ccp/web-mirrors/mondorescue/download/mondoarchive.1.html](http://ccp14.minerals.csiro.au/ccp/web-mirrors/mondorescue/download/mondoarchive.1.html)

Thanks so much for the reply BTW lcg!

:D

---

### Post by dcstar on 2005-11-27
[QUOTE=promet]Hello,
..........
So I was wondering, is there any software precaution possible to soften this sort of blow ( it WILL happen again ) and I always am of the mind to reinstall rather than get out the toolbox on a deeply corrupted system.

So if anyone has any suggestions (Other than creating a GRUB boot disk, which I've done) until I can scrape together the gelt for a UPS. I would be eternally grateful. And thanks.

Signed,
UBUNTU in the dark :???:[/QUOTE]
Check your /etc/hdparm.conf file and make sure **write_cache** is off for your HD, it may slow performance a little but it should make the system more robust when a power failure occurs.

---

### Post by promet on 2005-11-28
Hey dcstar,

Another, quite astute, suggestion. I will try this and measure the speed pros and cons (I'll probably hardly notice!). Thanks so much for taking the time to reply.

;)

---

