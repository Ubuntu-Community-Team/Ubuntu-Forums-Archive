---
title: "Help with SATA controller"
date: 2010-05-27
forum: Hardware
---

### Post by robmiracle on 2010-05-27
Hi.  I've got a computer from last century that I've put together.  Its a Dual processor P-III/550 with 768M of ram.  I had installed an IDE drive on as the Primary Master using the Motherboard's IDE interface.  I've got a DVD/writer as the Secondary Master.

The other day I got a boot failure error. Using a liveCD I was able to boot the machine and mount the drive and see it, etc.  I just couldn't boot from it.  

So I ordered a PCI SATA controller to use a SATA drive recovered from another dead computer. That drive had Ubuntu 9.04 installed on it (the computer I'm working with at the moment is 10.04).  I installed the card and the drive. 

When I boot up, I get the old IDE drive.  But amazingly, it actually booted today with no boot error.  It is /dev/sda1 btw.

I see /dev/sdb1 out there and I can mount it and access all the files.

Now to my question:  How can I make /dev/sdb1 the boot drive?  I would like to boot from it, get it upgraded to 10.04, mount /dev/sda1 (the drive thats getting flaky), copy content off of it that I want to keep and then get rid of the questionable drive.

Thanks
Rob

---

