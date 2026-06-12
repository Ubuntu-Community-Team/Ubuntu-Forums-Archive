---
title: "Hard Drive on a PowerBook G3"
date: 2010-08-12
forum: Hardware
---

### Post by DMD65 on 2010-08-12
Hi,
This is my first post. I have already searched the forums but could not find any relevant information on my problem as follows.
I planned to install ubuntu on my old PowerBook G3, bronze. It meets the requirements for installing the ubuntu in terms of memory and processor. My problem is rather the hardware. The Harddrive is erased but formatted as journaled by Disk Utility. CD drive is non-functional and the machine won't boot from the external cd drive. I tried to use the USB installation, pressing down alt and starting the machine, but it just shows two arrows and clicking on them won't lead anywhere. My question is simple: How can I get the machine t recognize the USB installation disc? Is this due to anyfirmware on the hardware, the PowerBook or should I try anythign else?
Grateful for any suggestions.

---

### Post by demonfoo on 2010-08-13
> **DMD65 said:**
> Hi,
This is my first post. I have already searched the forums but could not find any relevant information on my problem as follows.
I planned to install ubuntu on my old PowerBook G3, bronze. It meets the requirements for installing the ubuntu in terms of memory and processor. My problem is rather the hardware. The Harddrive is erased but formatted as journaled by Disk Utility. CD drive is non-functional and the machine won't boot from the external cd drive. I tried to use the USB installation, pressing down alt and starting the machine, but it just shows two arrows and clicking on them won't lead anywhere. My question is simple: How can I get the machine t recognize the USB installation disc? Is this due to anyfirmware on the hardware, the PowerBook or should I try anythign else?
Grateful for any suggestions.

Um, that's a pretty old machine now. What images are you using to try to install this machine? Machines of that vintage would not boot from USB. Also, if you're trying to boot an i386 image, that'll never work; a PowerBook G3 is based on a PPC 740/750 series chip, which is vastly different from an x86 processor. I've heard from a friend that the community-maintained PPC Ubuntu images are in a pretty bad state, so I wouldn't be surprised if getting Ubuntu installed on the machine is very difficult to impossible. :|

---

### Post by eqqfooyoung on 2010-08-13
I'm not an expert with macs, but it sounds like something with your EFI is messed up. Normally, you can restore this by using your mac osx disk, but since your CD drive isn't working, you need to do something else.

I found this article online which looks like it resets the startup disk selection among other things. Again, I don't know enough about this to specifically say this is what you should do, but it might be something you could look into.

[http://support.apple.com/kb/ht1379](http://support.apple.com/kb/ht1379)

Good luck.

---

### Post by demonfoo on 2010-08-13
> **eqqfooyoung said:**
> I'm not an expert with macs, but it sounds like something with your EFI is messed up. Normally, you can restore this by using your mac osx disk, but since your CD drive isn't working, you need to do something else.

A PowerPC-based system doesn't have EFI. It has OpenFirwmare (IEEE 1275-1994). If he's using an x86 boot image (and I have a sneaking suspicion he is), it's not going to be able to boot.

---

