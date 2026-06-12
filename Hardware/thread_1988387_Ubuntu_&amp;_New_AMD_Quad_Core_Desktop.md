---
title: "Ubuntu &amp; New AMD Quad Core Desktop"
date: 2012-05-27
forum: Hardware
---

### Post by GeosUser on 2012-05-27
Hello,
I'm ordering a new desktop PC from cyberpowerpc and am considering skipping Windows7 in favor of Ubuntu.  What I want to do is end up running WindowsXP and Office2000 using VMWare on this PC.  I have extensively custom Excel spreadsheets that are critical to my business.  Before I finalize my PC order, I'd greatly appreciate some advice about using Ubuntu on the following hardware.  Thank you in advance for your help.
Hardware list:
Case: Cooler Master HAF 912 Mid-Tower Gaming Case w/ Adjustable HDD Cage (Black Color) [-25]
CPU: AMD FX-4170 4.20 GHz Quad-Core AM3+ CPU 4MB L2 Cache & Turbo Core Technology [+30]
Cooling Fan: Asetek 510LC Liquid Cooling System 120MM Radiator & Fan (Enhanced Cooling Performance + Extreme Silent at 20dBA) (Single Enermax Enlobal Silent High Performance 120MM Fan [+15])
Motherboard: [CrossFireX] ASUS M5A97 AMD 970 Chipset CrossFireX Support DDR3 Socket AM3+ ATX w/ 7.1 Audio, GbLAN, USB3.0, SATA-III, RAID, 2 Gen2 PCIe, 2 PCIe X1, & 2 PCI
Memory: 8GB (4GBx2) DDR3/1333MHz Dual Channel Memory [+18] (Corsair or Major Brand)
Video Card: NVIDIA GeForce GT 520 1GB 16X PCIe Video Card (Major Brand Powered by NVIDIA)
Power Supply Upgrade: 500 Watts - Standard Case Power Supply [+22]
Hard Drive: 500GB SATA-III 3.0Gb/s 16MB Cache 7200RPM HDD [-17] (Single Drive)
Optical Drive: 24X Double Layer Dual Format DVD+-R/+-RW + CD-R/RW Drive (BLACK COLOR)
Sound: * ASUS Xonar DG 5.1 Channels PCI Xonar DG Sound Card [+29]
Network: Onboard Gigabit LAN Network
Flash Media Reader/Writer: INTERNAL 12in1 Flash Media Reader/Writer [+10] (BLACK COLOR)
Internal USB Port: Built-in USB 2.0 Ports

---

### Post by MonkeyPaw on 2012-05-27
Honestly, I don't think you'll have many issues, though the question for me is what you plan to do with the machine? If you are just wanting a good desktop experience, have little intent on playing games, and plan to run just one monitor, then I suggest getting a Core i5 setup with integrated graphics. That way you won't need to fiddle with nVidia or AMD proprietary drivers, and you'll save some electricity as well. Regardless, your hardware seems pretty straightforward and should load Ubuntu fine. I don't think you need the sound card, as the motherboard's integrated sound should work just fine. The integrated Realtek stuff seems to work great on Ubuntu.

Also, if you haven't purchased VMware, you might have luck with VirtualBox, which is free and works pretty good on Ubuntu. I use VirtualBox to load XP when I need to use some random unsupported device (like my kids leapfrog).

---

### Post by Yellow Pasque on 2012-05-27
The Xonar DG is a nice upgrade over onboard audio if you have good speakers/headphones, but recording and front panel headphone jack are not working on the Xonar DG.

---

### Post by gordintoronto on 2012-05-27
If you don't plan to overclock the CPU, you absolutely do not need liquid cooling.

I suggest you post your config on PCMech.com. They will suggest you go with a WD "black" hard drive. The HAF 912 doesn't come with a power supply, they will suggest you get a really good power supply, such as an Antec "EA" series supply. It might cost a few bucks more, but it's a good way to avoid problems.

If you don't play Windows games, your choice of video card makes a lot of sense. I built a system a couple of years ago, put money into the CPU, not the video card.

---

### Post by GeosUser on 2012-05-28
Hello,
Thanks to all for your helpful replies.  I am a trader and I use Excel and several Excel-specific add-ons to support my own custom technical analysis.  I also use a program called QuoteTracker to do my trading.  I prefer not to use the software provided by the online brokerages plus I'm able to use QuoteTracker to feed real time quote data to my Excel models.  I don't want to use Windows7 or the new version of Office because of the uncertainty and labor involved in the conversion process.  Hence my desire to use Ubuntu and then replicate my current trading set-up as a virtual PC.  I have Ubuntu running on 2 Dells, a netbook and notebook and find it far superior to WindowsXP on both.  My wife has an HP desktop running Windows7, so I have had exposure to it.  I don't do any gaming, social media or other non-trading related work on my "trading" WindowsXP desktop.  My goal is to have a stable PC that allows me to exactly recreate my current setup on top of an Ubuntu base.  Thank you.

---

### Post by kurt18947 on 2012-05-28
I'm an AMD fan and if you want a discreet video adapter,  I've disabled onboard video on 2 AMD boards and added Nvidia graphics cards - GS8400 and GeForce 210 - with no problem whatsoever.  My concern would be about security issues related to unsupported Office 2000 and soon-to-be-unsupported XP.   Is this of any concern to you?  Will running in a VM alleviate any concerns?  I'm no expert but these are questions I'd consider if I were in your position.

---

