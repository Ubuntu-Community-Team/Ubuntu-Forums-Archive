---
title: "Sis 771/671 tty functionality"
date: 2012-03-14
forum: Hardware
---

### Post by GJJ on 2012-03-14
Hi there,

I have a problem with the tty's in Xubuntu 11.10 64-bit ([all variants] because I also had this problem with ubuntu). I have a Sis 771/671 video adapter, and I use the drivers provided here: [http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)

I know this is a very nasty video adapter, and tty functionality has never worked. Up until today I accepted that this was just a problem with the video adapter, but today I noticed something strange. After connecting a 1280x1024 screen to the laptop and rebooting, the tty's worked. Furthermore, the Xubuntu boot splash appeared to be of higher resolution.

However, upon rebooting without the secondary monitor, the screen went back to the way it was before, without functioning tty terminals. Now I can't always have the secondary monitor connected, but I would still like to use the tty's.

I'm wondering whether there is a GRUB flag or boot option I can set to get tty's always working. I suspect it has to do something with GRUBs VGA setting, but I'm wondering if anyone has any specific ideas. 

Thanks in advance.

GJJ

---------------
Relevant lspci output

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```

---

### Post by GJJ on 2012-03-14
Solved it! For future reference: I installed startup-manager and set both the display resolution and the bootloader menu resolution to 1024x768 and this solved the problem.

(Thread can be deleted.)

GJJ

---

### Post by Pjotr123 on 2012-04-29
This is a better solution, because it uses a new driver:
[http://sites.google.com/site/easylinuxtipsproject/sis](http://sites.google.com/site/easylinuxtipsproject/sis)

Quite easy! :-)

---

