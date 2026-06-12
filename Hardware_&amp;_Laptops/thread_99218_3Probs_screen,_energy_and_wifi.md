---
title: "3Probs: screen, energy and wifi"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by Goldenice on 2005-12-05
Hi everyone and sorry for my bad english.

Before learning a little about linux with my previous gentoo, I decided to install breezy because of installation times. Both Gentoo and Breezy had the same problems. I have a Dell Latitude D505 Laptop with WSXGA screen and these are some lines of my lspci I expect are useful for anyone who want's to help me:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

1.- My screen has a 1400x1050 resolution, but in linux I can only get 1280x1024. In my Screen section of my xorg.conf i have in all colour depth 1400x1050 and i have no idea why it only takes 1280x1024.

2.- I have to say that in gentoo i didn't try to configure energy so i have no idea to configure it. In system Settings I've configured the power button to hybernate but when I press it i get a beautyful laptop powered off. Anyone has a manual?

3.- I use ndiswrapper because there is no suport for broadcom wireless in kernel (at least on early 2005). It runs well when i have my laptop pluged in. If not, it freezes everything trying to modprobe ndiswrapper and i have to press the power button 5 secs. After a long time of testing i become aware of before rebooting it runs. Anyone knows why?

Thanks a lot.

---

### Post by Rollmops on 2005-12-05
[QUOTE=Goldenice]1.- My screen has a 1400x1050 resolution, but in linux I can only get 1280x1024. In my Screen section of my xorg.conf i have in all colour depth 1400x1050 and i have no idea why it only takes 1280x1024.[/QUOTE]
look for 855resolution.

---

### Post by hedone on 2005-12-05
for sleep u can find solution on this forum... and yes... quite good one!!! but i have some problems wakeing up my graphics... [here is one of good links about suspend]("http://ubuntuforums.org/showthread.php?t=79507&highlight=sleep.sh")


and ndiswrapper... 
ndiswrapper -l to see if ur driver is on
ndiswrapper -m to make alias
modprobe ndiswrapper to start it!

try to add ndiswrapper to modprobe by editing modprobe with gedit! and then best solution is to install NetworkManager when ndiswrapper works...

---

