---
title: "Any USB device inserted causes a crash or slowdown."
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by user_of_gnomes on 2006-02-12
Hello, 

Whenever I insert the following USB devices:

[list]
[*]USB mouse - slowdown if restarted - functions normally when inserted after boot is complete.
[*]KVM switch - Slowdown if restarted - not hot swappable due to PS/2 emulation
[*]FHD2-Pro (FAT32) - Crashes Linux - IRQ error I no longer recall/refuses to boot
[/list] 

Things go haywire. 

When I restart the PC and insert either the USB mouse or the KVM switch, after the time has been synchronized with a timeserver, I get an error that tells me "Don't bother (Try using IRQPOLL upon restart) and it lists my VIA-RHINE network adaptor, the USB device currently inserted and then tells me it has 'dropped' IRQ 5 or 11. 

I double checked the BIOS and disabled USB legacy support. Had no effect whatsoever. The rest is properly configured, because Windows XP had no trouble with the same motherboard, HDD, RAM and processor inserted. 

I'm considering to start using Windows XP again as I am getting a wee-bit desperate regarding my far too expensive KVM switch.

---

### Post by user_of_gnomes on 2006-02-14
I failed to mention that Linux will not crash when I insert my 256MB Kingston USB stick. 
However, I have never reset the computer whilst the stick was mounted. I only mounted and unmounted it when Linux had fully booted.

---

### Post by HanZo on 2007-02-19
I don't know how to help you... but I have a similar problem here... no matter what I stick into the USB port, ubuntu instantly freezes. this on a fresh install on a new custom made system. (AMD Sempron, ATI 9250 pro card, Asus MoBo, Edgy). Of course I haven't got this problem with windows.

---

### Post by user_of_gnomes on 2007-02-19
Thanks for your reply, Hanzo. I 'resolved' this problem quite a while ago with the help of the members of the Dutch Ubuntu forum. Turned out my USB controller was fried and I ended up replacing the mainboard. That definitely did solve the problem.

---

