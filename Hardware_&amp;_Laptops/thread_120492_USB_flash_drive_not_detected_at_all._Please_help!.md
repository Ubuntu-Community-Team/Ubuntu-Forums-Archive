---
title: "USB flash drive not detected at all. Please help!"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by JDElectric on 2006-01-21
I've been searching for a couple days now to find an answer to this with no luck!  I'm a new Linux user, with so far a week under my belt with Ubuntu.  
I've got everything working the way I want except the USB port.
In all my searching I've found that there seems to be a common problem getting USB devices to work properly with Breezy, but I'm hoping someone here can help.

Background:
I'm using Breezy 5.10 on a IBM Thinkpad 390E.  I've noticed on boot-up when it gets to the step "Starting Hotplug Subsystem" it continues on to the next step without displaying "OK".  I've made sure all the packages related to usb and mounting are installed.  I've checked the BIOS settings.  I've tried booting with a Puppy Linux Live CD and my USB flash device is detected and works fine.  I'm using a Sandisk Cruzer Mini 256MB.  When I plug it in, it doesn't light up at all.

Very frustrated here.  I've spent way too much time on this already.

Any help would be greatly appreciated.

Thanks,

---

### Post by roe on 2006-02-08
Hi JDElectric
Search in synaptic to check if " usbmount" is installed if install it and see if it helps.

---

### Post by BarryTice on 2006-12-05
I also have a 390E. I started with RedHat 8, and couldn't get the USB to work. I moved to RedHat 9 on it and somewhere found something (I don't remember what...) that let the USB work.

I later moved to Ubuntu (a good move, I might add...) Hoary Hedgehog, and lost my USB accessibility.

Two nights ago I replaced Hoary with Edgy Eft and on a whim I plugged my USB MP3 player in, and it recognized it and automounted it with no problem. (You may have to download the Alternate installer. I did, but I only have 128 MB.)

I never ran Badger, so I don't know how many of the improvements I'm seeing are newer than that. But if you upgrade to Edgy you may find (as I did) that the USB flash drive issue is now working for you.

Hope this helps.

-- BarryTice

---

