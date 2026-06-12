---
title: "A good video card and SATA RAID Controller"
date: 2008-06-03
forum: Hardware
---

### Post by pancakelizard on 2008-06-03
From what I've read on here, LaunchPad and other internet sites, the Nvidia Geforce 8500gt is not working (and probably never will work) with Ubuntu or Kubuntu. After several mind numbing days, I'm about to just throw in the towel with it.

This is the launchpad URL:
[https://answers.launchpad.net/ubuntu/+question/9982](https://answers.launchpad.net/ubuntu/+question/9982)

Here is my support thread on here:
[http://ubuntuforums.org/showthread.php?t=814819](http://ubuntuforums.org/showthread.php?t=814819)

I will sell the card on ebay and purchase another one. But I need to know what is a good graphics card (not expensive) that is pci-e 16x, has dvi (prefer dual dvi for later upgrade but not needed) and will work with Ubuntu 8.04 without a huge headache.

-----------
Also, I was going to use this card for RAID 1:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815158036](http://www.newegg.com/Product/Product.aspx?Item=N82E16815158036)

But it gives me abunch of problems so I am using my onboard SATA connectors and using mdadm for fakeraid. I also have 4 drives I need to setup for RAID 5 and since I'm using fakeraid, I would like to just get one card.

I was thinking of this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009](http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009)

And I have this motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034)

Now here is what I am confused on. For the controller card, it states I need a "64-bit PCI-X133MHz" slot but my motherboard specs only state I have:

PCI Express x16 1
PCI Express x1 	2
PCI Slots 	4

Are PCI Slots assumed to be 64-bit 133mhz or is my board not compatible with the part? If so, what is a good recommendation for a SATA controller card with 6-8 internal SATA 2 connections that will work in Linux?

---

### Post by ilrudie on 2008-06-03
Just my opinion here and granted I don't know what you are trying to do with your RAID 5 array but just stick with the software RAID.  It might be easier to recover should your SATA/RAID controller fail.  You could get whatever brand you want without having to worry if its compatible with your old controller.  If your mind is made up that you want hardware RAID sorry to waste your time I don't know about Linux RAID controllers.

---

### Post by pancakelizard on 2008-06-03
Right, I am going to use Linux software RAID but wanted to know of a good compatible SATA 2 controller with atleast 6 SATA 2 ports.

Also, anyone have any suggestions for the video card?

---

### Post by stchman on 2008-06-03
> **pancakelizard said:**
> From what I've read on here, LaunchPad and other internet sites, the Nvidia Geforce 8500gt is not working (and probably never will work) with Ubuntu or Kubuntu. After several mind numbing days, I'm about to just throw in the towel with it.

This is the launchpad URL:
[https://answers.launchpad.net/ubuntu/+question/9982](https://answers.launchpad.net/ubuntu/+question/9982)

Here is my support thread on here:
[http://ubuntuforums.org/showthread.php?t=814819](http://ubuntuforums.org/showthread.php?t=814819)

I will sell the card on ebay and purchase another one. But I need to know what is a good graphics card (not expensive) that is pci-e 16x, has dvi (prefer dual dvi for later upgrade but not needed) and will work with Ubuntu 8.04 without a huge headache.

-----------
Also, I was going to use this card for RAID 1:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815158036](http://www.newegg.com/Product/Product.aspx?Item=N82E16815158036)

But it gives me abunch of problems so I am using my onboard SATA connectors and using mdadm for fakeraid. I also have 4 drives I need to setup for RAID 5 and since I'm using fakeraid, I would like to just get one card.

I was thinking of this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009](http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009)

And I have this motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034)

Now here is what I am confused on. For the controller card, it states I need a "64-bit PCI-X133MHz" slot but my motherboard specs only state I have:

PCI Express x16 1
PCI Express x1 	2
PCI Slots 	4

Are PCI Slots assumed to be 64-bit 133mhz or is my board not compatible with the part? If so, what is a good recommendation for a SATA controller card with 6-8 internal SATA 2 connections that will work in Linux?

According to this site the 8500GT works with the 173.14.05 drivers.

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html)

I don't know when the 173.14.05 will be in the repos, but you can always install them yourself.

---

