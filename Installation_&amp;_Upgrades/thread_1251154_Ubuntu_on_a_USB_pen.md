---
title: "Ubuntu on a USB pen"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by goseph on 2009-08-27
I need a portable linux on a USB pen,
Any computers that this USB linux is plugged into will be quite new with loads of memory etc.

Given these... should I go for Ubuntu or Ubuntu netbook remix or Xubuntu or......(DSL??). Will the booting from a USB pen make the whole thing run slowly or can it boot and then run entirely in memory?

---

### Post by coldReactive on 2009-08-27
Search google for **Ubuntu persistent USB**. Don't just use the ISO with the USB Live Creator or whatever.

---

### Post by stlsaint on 2009-08-27
see [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by utnubuuser on 2009-08-27
I bought one of the USB sticks available through the Ubuntu store.  Works perfectly.

---

### Post by Mighty_Joe on 2009-08-27
> **goseph said:**
> 
Given these... should I go for Ubuntu or Ubuntu netbook remix or Xubuntu or......(DSL??). 

Just for the record, UNR is specifically for netbooks with the Atom processor ([see here]("http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix#Specifications")).  

> **goseph said:**
> 
Will the booting from a USB pen make the whole thing run slowly or can it boot and then run entirely in memory?

Running the Live CD from USB ([see here]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator")) is slow because it's a compressed file system and has a lot of data to swap through the USB bus.  A full install on a USB drive isn't terribly slow.  On a modern machine, I doubt you could tell the difference between the various *buntus (except, of course, for the obvious graphic elements). DSL would probably be faster loading just because it's so small. 
See [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") for the various options, and my post on that topic for the procedure I use to do a full install.

---

### Post by TheShabz on 2009-08-27
Hey all. Posting in this thread so I dont have to make another one.

I followed the steps on pendrivelinux for persistent USB booting for 9.04. even though the .bat said all was well, it would not boot from usb. the computer is set to boot from usb first (went back and manually selected it as well) but the system would not recognize it and try PXE boot from the network. 

I have successsfully been able to boot other distros on this computer but ubuntu J is givng me issues. Solutions?

---

