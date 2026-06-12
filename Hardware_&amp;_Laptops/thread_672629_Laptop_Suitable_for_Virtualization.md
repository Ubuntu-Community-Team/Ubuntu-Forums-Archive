---
title: "Laptop Suitable for Virtualization"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by gdwatson on 2008-01-19
I'm not entirely certain whether this belongs here or in the virtualization forum.  (If it belongs there, would someone be kind enough to move it?)

I'm contemplating buying a laptop in the near future, and I'd like it to run Linux (ideally Ubuntu, which is what I'm running on my desktop).  But I need to run some Windows applications also.  Dual-booting is a possibility, but virtualization really appeals to me as a solution.

Can anyone recommend any laptops whose hardware is solidly supported by Linux, which have hardware support for KVM and support enough RAM to do it properly?  Ideally such a laptop would come with a real XP install disk/key.  (In laptop Shangri-La, it would also have a good keyboard, good portability and good battery life.)

Any suggestions?

---

### Post by mzembe on 2008-01-19
[http://wiki.xensource.com/xenwiki/IntelVT](http://wiki.xensource.com/xenwiki/IntelVT)


[http://www.intel.com/technology/itj/2006/v10i3/3-xen/4-extending-with-intel-vt.htm](http://www.intel.com/technology/itj/2006/v10i3/3-xen/4-extending-with-intel-vt.htm)

---

### Post by gdwatson on 2008-01-20
The Dell Inspiron 1420n is an attractive option.  Does anybody know if its BIOS supports the Intel VT extensions or disables them?  Google doesn't seem to be helping me out here.

---

### Post by FrankVdb on 2008-01-20
I have a Dell XPS M1330 and I'm running Gutsy on it without much problems with XP virtualized in a VirtualBox virtual machine. XP works without noticeable lag. Starts in seven seconds time!

The only problem I have is that suspend mode does not work. 

Specs: 2.2 GHz dual core, 2 gigs of RAM (the virtual machine uses 512 megs of that), 200 Gb 7200 rpm harddisk.

---

### Post by gdwatson on 2008-01-20
Awesome, thanks!

---

