---
title: "Recommended PCI eSTATA card?"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by sgarman on 2007-10-01
Hi all,

Can anyone recommend a SATA controller PCI card that meets the following requirements?:

* Compatible with Ubuntu Feisty Fawn or later (Feisty uses kernel 2.6.20).
* Has at least one external SATA port.
* Is available on NewEgg.com.

I'm just looking for something simple to use with an external hard drive that has an eSATA port.

Thanks,

Scott

---

### Post by sgarman on 2007-10-01
In another forum I received a recommendation indicating that the Addonics AD2SAP-E worked well under Feisty. 

[http://www.addonics.com/products/host_controller/ad2sap-e.asp](http://www.addonics.com/products/host_controller/ad2sap-e.asp)

I have ordered it and will post an update when I've tried it out.

Scott

---

### Post by say2sky on 2007-10-03
> **sgarman said:**
> In another forum I received a recommendation indicating that the Addonics AD2SAP-E worked well under Feisty. 

[http://www.addonics.com/products/host_controller/ad2sap-e.asp](http://www.addonics.com/products/host_controller/ad2sap-e.asp)

I have ordered it and will post an update when I've tried it out.

Scott

Have you installed Feisty into your eSATA hard drive and boot directly from it? I am also interested in this but I am not sure I should buy a new Mboard with eSATA or just buy a PCI-E eSATA. Boot from eSATA hard drive need BIOS support? I hope eSATA is not just used as a backup device.

---

### Post by onesojourner on 2007-10-03
I have a roswell that I bought from new egg. I am running 7.04 on my desktop. I plugged it in put in a 500g hdd and it worked like a charm. The only thing is I have to go into media and right click and mount it every time I reboot. I am sure there is a way for it to mount on start up but I only turn it off every 2 weeks or so, so its not an issue.

---

### Post by sgarman on 2007-10-11
> **say2sky said:**
> Have you installed Feisty into your eSATA hard drive and boot directly from it? I am also interested in this but I am not sure I should buy a new Mboard with eSATA or just buy a PCI-E eSATA. Boot from eSATA hard drive need BIOS support? I hope eSATA is not just used as a backup device.

No, I'm just using the eSATA drive for nightly backups of my workstation. However, I can tell you that this Addonics card has its own BIOS and I'm pretty sure can become bootable.

It turns out this card is giving me some bootup headaches regarding GRUB. It looks like because the drive is detected early on by the BIOS, it's changing my hard drive device ordering. I'm still trying to sort that out in this thread:

[http://ubuntuforums.org/showthread.php?p=3517393](http://ubuntuforums.org/showthread.php?p=3517393)

Scott

---

