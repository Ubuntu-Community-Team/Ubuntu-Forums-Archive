---
title: "Unbuntu under MS Virtual PC 2007?"
date: 2008-08-23
forum: General Help
---

### Post by clevermax on 2008-08-23
Hello Everyone,

Has anybody managed to get Ubuntu running in Microsoft Virtual PC 2007 in a Vista box?  Whenever I start Ubuntu under Virtual PC, I get an error saying that and illegal operation has been executed and virtual PC quits. 

I tried suggestions like the VGA mode etc. But nothing seems to work.

Any help for getting Ubuntu running under Virtual PC greatly appreciated.

Thanks In Advance,
J

---

### Post by dje on 2008-08-23
try this guide [here]("http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/")

if that fails try [VirtualBox]("http://www.virtualbox.org/"), which IMO is much better

dje

---

### Post by clevermax on 2008-08-23
> **dje said:**
> try this guide [here]("http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/")

if that fails try [VirtualBox]("http://www.virtualbox.org/"), which IMO is much better

dje


For me, the step two of the guide (Safe graphics mode and enter) fails. Messgaebox says "An unrecoverable processor error has been encountered". 

Guess I have to try VirtualBox.

Thanks,
J

---

### Post by clevermax on 2008-08-24
> **clevermax said:**
> For me, the step two of the guide (Safe graphics mode and enter) fails. Messgaebox says "An unrecoverable processor error has been encountered". 

Guess I have to try VirtualBox.

Thanks,
J

Tried the virtualbox and it works. :)
But I am not able to change the resolution above 800*600. Any idea why?

---

### Post by dje on 2008-08-24
glad its working :), you must install the guest additions to increase the screen resolution and gain other features. there is a nice guide to installing the guest additions [here]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/")

dje

---

### Post by clevermax on 2008-08-24
> **dje said:**
> you must install the guest additions to increase the screen resolution and gain other features. 

I was wondering if there's any download link available for the guest additions iso image. How big is it? I am worried about its size as I have an internet connection with a dtata transfer limit at home, so I have to downlaod it from elsewhere, may be from Office :)

---

### Post by dje on 2008-08-24
try searching on google but the iso isnt huge, around 10mb

dje

---

### Post by gaussian on 2008-08-24
> **clevermax said:**
> I was wondering if there's any download link available for the guest additions iso image. How big is it? I am worried about its size as I have an internet connection with a dtata transfer limit at home, so I have to downlaod it from elsewhere, may be from Office :)


If should already exists at:
/usr/share/virtualbox/VBoxGuestAdditions.iso

---

### Post by dje on 2008-08-24
> **gaussian said:**
> If should already exists at:
/usr/share/virtualbox/VBoxGuestAdditions.iso

I don't think it did for me. When I went to Devices >> Install guest additions it told me I didn't have and asked if I wanted to download it

dje

---

### Post by gaussian on 2008-08-24
One more thing: you probably want the non-open source version straight from Sun not the one from the repos. More things (like USB support) should work that way.

---

