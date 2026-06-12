---
title: "finally got all my hardware working"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by cmat on 2007-05-15
My Acer Aspire 5040 proved to be quite a challenge for me to get working. However, I got the sound and wireless Wi-Fi working flawlessly. I fixed the problem with the sound by compiling the latest ALSA drivers and installing them. The problem I've had with this was that I never did the compile and installation as root and didn't see the errors saying "Permission Denied". I assumed it installed correctly but it did not. Make sure you used "sudo -i" which gives you full root access. I got the Wi-Fi working by buying a D-Link WNA-1330. As soon as it was installed, MadWIFI detected it and I was on the internet as soon as I booted up. Although, Ubuntu detected my onboard Atheros card, MadWIFI did not. The card was $50 Canadian and much better then my onboard. So I hope my little success story would shed some light on the problems other people are having and give more legitimacy to running Linux on the laptop with hardware designed for windows.

---

