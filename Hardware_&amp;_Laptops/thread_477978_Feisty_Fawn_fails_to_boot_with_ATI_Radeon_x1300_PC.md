---
title: "Feisty Fawn fails to boot with ATI Radeon x1300 PCI"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Sirin on 2007-06-18
Hello, I recently got a 256MB ATI x1300 PCI card (my mobo doesn't have AGP or PCI-E, so this is the best I can get :( ), and wanted to use it with Ubuntu in place of my old 64MB Intel 865 IGP. When I tried to boot it up, it went to the splash, but not even halfway there, the bar ceased to move. I tried waiting and waiting for it to boot, but to no response. Strangely, my card works with PC-BSD and of course, with Windows...

Sadly, I can only run Ubuntu with my Intel IGP (which sadly cannot run Beryl very well :( ). Does anyone have any solutions for this?

---

### Post by Sirin on 2007-06-20
Anyone? :(

---

### Post by Kubunteando on 2007-06-20
What drivers have you installed?

Have you tried the last 8.37 from ATI?

---

### Post by Sirin on 2007-06-22
> **Kubunteando said:**
> What drivers have you installed?

Have you tried the last 8.37 from ATI?

I can't even boot into Ubuntu to install any drivers, sadly. :(

---

### Post by Kubunteando on 2007-06-22
Can you post these 2 files:

- /etc/X11/xorg.conf
- /var/log/Xorg.0.log

There we should have some hints on what is wrong.

---

### Post by bone43 on 2007-06-22
> **Sirin said:**
> Hello, I recently got a 256MB ATI x1300 PCI card (my mobo doesn't have AGP or PCI-E, so this is the best I can get :( ), and wanted to use it with Ubuntu in place of my old 64MB Intel 865 IGP. When I tried to boot it up, it went to the splash, but not even halfway there, the bar ceased to move. I tried waiting and waiting for it to boot, but to no response. Strangely, my card works with PC-BSD and of course, with Windows...

Sadly, I can only run Ubuntu with my Intel IGP (which sadly cannot run Beryl very well :( ). Does anyone have any solutions for this?

Yes read this and install with the alternate CD...

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

;)

---

