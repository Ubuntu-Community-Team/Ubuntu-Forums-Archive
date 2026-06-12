---
title: "Brand New Dell m1330 unusable in 8.10"
date: 2009-01-17
forum: Hardware
---

### Post by Zelbinian on 2009-01-17
Hey everyone. I've seen a bunch of posts about this laptop on these forums, but nothing seems to specifically get at my issue. Here's my steps:
[LIST]
[*]I tri-boot: Vista, Windows 7, Ubuntu 8.4 installed in that order (all 64-bit)
[*]Loaded up Ubuntu and upgraded to 8.10
[*]On startup, GRUB gives me two Linux kernel options: 2.6.27-9-generic and 2.6.24-23-generic; I don't know why I get two
[*]So far, I've enabled the proprietary Broadcom driver, but not the Nvidia driver
[*]Within a few minutes, the screen either locks up or, if I keep moving the mouse on the trackpad, the screen doesn't lock up but the system becomes almost completely unresponsive
[/LIST]

Any ideas?

---

### Post by taurus on 2009-01-17
The older kernel is from hardy and the newer one is from intrepid.  

What graphic card does it have and have you looked in System -> Administration -> Hardware Drivers to see if it's on the list?

---

### Post by Zelbinian on 2009-01-17
It's a GeForce 8400M GS. 

I had found a thread somewhere about those chips being a bit faulty for awhile and causing Ubuntu to lock up, but the thread also stated that the problem had been fixed around the time of writing (which was about September if memory serves). Also, neither version of Windows has any trouble.

---

