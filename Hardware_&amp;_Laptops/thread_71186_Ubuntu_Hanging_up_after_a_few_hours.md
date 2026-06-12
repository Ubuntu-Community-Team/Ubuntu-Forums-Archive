---
title: "Ubuntu Hanging up after a few hours"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by fortytwo on 2005-10-02
Hey guys,
My Windows install got hosed a couple of weeks ago, so I thought I'd finally take the plunge and go linux full time.  

I put on Kubuntu 5.04 but noticed that when I left the machine on for a while (4-5 hours probably) and then came back, it was ridiculously slow and I had to reboot to get normal functionality back.  After a while, I thought maybe I'd try the Breezy preview version, thinking *maybe* something in Kubuntu was causing the problem, but I'm still having the same problem.  

The only recent addition I'd made to the machine was to add some more memory to the machine (now 1 gig) but Windows never had any trouble with hanging up when the new memory was installed, so I'm not sure if that's the issue.

Does anyone have any suggestions on this issue?  I'd love to stay with Linux full time, but at this rate I may be forced to put Windows back on...

Thanks

---

### Post by Teroedni on 2005-10-02
can your post your cpu graphics board etc ?

---

### Post by fortytwo on 2005-10-02
My graphics card is an nvidia GeForce FX 5200 and my CPU is an Intel 2.2 Ghz, it's kind of hard to tell the exact specs from the device manager...is there a better place to look?

Thanks for the reply

---

### Post by Teroedni on 2005-10-02
Have you installed after the memory upgrade or before it?
Have you nstalled any programs after Ubuntu install?

---

### Post by fortytwo on 2005-10-02
The memory upgrade came before installing Linux.  I installed it when I was running Windows and had no problems.

I haven't installed anything major after installing Linux.  I put on the 5.1 preview release, and did an upgrade, but not really anything after that.

---

### Post by Teroedni on 2005-10-02
hmm strange:confused: 

What do you mean by slow?
does the pointer moves slowly or does program takes longer to load?

---

### Post by fortytwo on 2005-10-02
Well, the mouse pointer will move around alright, but actually doing anything is really lagged.  For example, I try to run top to see what's going on, and I can type in 'top' fine with no lag, but then I sit and wait a few minutes for it to open, and then it takes forever to update.  

Thanks for the help

---

### Post by fortytwo on 2005-10-17
I believe I've fixed this problem by disabling apic.  I did this by adding 'noapic' and 'nolapic' to my kernel boot line.

---

