---
title: "Acer Asprire 5002 WLMi Hardware Problems"
date: 2009-03-19
forum: Hardware
---

### Post by linux_burner on 2009-03-19
Folks,
I just installed Ubuntu on my laptop last evening. My Windows XP got infected with nasty Trojan agents and there was no way I could get rid of it. I did not want to go back to Windows, so installed Ubuntu. I am a noob to Linux. I think most of my hardware got detected during installation except display and wireless. I have to mention at this point that I had to format my Windows partition & overwrite that with Linux files.

Ubuntu detected my monitor and its resolution correctly but when I open image files, it looks like the setting is at 16bit and I did not find any tab in display to change it. I would like some help on how to get the display right.

My wireless card did not get detected during the setup. My wireless indicator light on my laptop does not even light up. I have tried several times to switch it ON but it just refuses. I did got through Wiki's ndiswrapper guide but could not follow everything (sorry a linux noob here). 

I just downloaded the windows drivers for VGA & Wireless (they r zip files). I need some instructions on where to place them and how to make Linux detect them. I would appreciate help on these things folks. It has been over a week since my laptop has functioned normally. I tried real hard to get rid of those Trojans but they took over windows pretty darn well and I just want to get Linux working so that I can continue to do basic stuff on my laptop.
Thanks,
-Vishak

P.S: My laptop's Hardware Config:
# AMD Turion 64 ML-30 processor (1 MB L2 cache, 1.6 Ghz)
# 15.4" WXGA CrystalBrite TFT LCD
# 100 GB Toshiba MK1031GAS Hard drive (4,200 rpm) [80GB hard drive (4,200 rpm)]
# DVD-Dual (DVD RW/CD-RW)
# 1 GB DDR [512MB]
# SiSM760GX graphics card
# 8-cell Battery
# 802.11b/g wireless

---

### Post by linux_burner on 2009-03-19
OK, I am answering my own post :)

My wireless problem is solved. Managed to get it working but display still sucks...

I tried "sudo dpkg-reconfigure xserver-xorg" and it did not ask me to config display properties. I don't know what else to do...I think my color depth should be set to 24bit but I do not know where and how to do it in GUI. Please help...Ubunto is almost there for me except for this one...

---

