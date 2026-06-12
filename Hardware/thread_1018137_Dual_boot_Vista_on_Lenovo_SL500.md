---
title: "Dual boot Vista on Lenovo SL500"
date: 2008-12-21
forum: Hardware
---

### Post by zatlite on 2008-12-21
Hi, would like your help dual-booting ubuntu with vista on the SL500 laptop.

I've seen a few people on the forums already who've done it so would be great if one of you put up a guide for the process. 

I've hit a brick wall at the part where I try to reinstall vista on the machine. The machine refuses to boot from the vista dvd. From what I've googled, I'm sure there are other weird things like needing SATA drivers etc.  

Thanks.

---

### Post by Captain_tux on 2008-12-22
Microsoft operating systems don't like to play well with other operating systems unless they're installed first... I suggest to install Vista first, then install Ubuntu.

But if you can't even boot from the DVD... check your BIOS to make sure your laptop is set to boot from the DVD first and not the hard drive.

Buena suerte!

---

### Post by tubbygweilo on 2008-12-22
> **zatlite said:**
> ....

I've hit a brick wall at the part where I try to reinstall vista on the machine. The machine refuses to boot from the vista dvd. From what I've googled, I'm sure there are other weird things like needing SATA drivers etc.  

Thanks.

zatlite,
The first time I tried installing Ubuntu onto an existing Vista machine (ThinkPad R61e) using the alt install disk (8.04?)  it also resulted in a ThinkPad that would not boot, I can not remember the exact error message but my new ThinkPad was well and truly bricked. After a bit of research I discovered this was due to the resize tool within the alt install killing the Vista boot and file manager system. 

This I recovered and fixed using the Lenovo care option (by hitting the ThinkVantage button on your SL500) at boot time which reset the ThinkPad back to a factory fresh state and from what I can remember this took a good few hours. While the hiden ThinkVantage/IBM/Lenovo recovery partition was going through it's paces I took the advantage of NOT loading third party/OEM anti-virus, browser bar additions and other unwanted offers. Once I again had a working Vista system I applied all Vista and Lenovo updates and again backed up the system to a number of DVDs, something that takes and age but is well worth doing. 

I then set about shrinking the [Vista file system]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista") so as to allow me the space in which to install a Ubuntu system using the alt install disk. 
As to disk size, install options and things you require for your Ubuntu installation I can offer no better help than that you browse the forum searching for dual boot, so good luck with your searching.

PS for sl500 or ThinkPad specific help a trip to the [ThinkPads Forum]("http://forum.thinkpads.com/") is often a good idea.

---

