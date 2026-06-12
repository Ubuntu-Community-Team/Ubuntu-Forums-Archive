---
title: "Laptop MSI GE70 2OD - no audio when connected to tv via HDMI"
date: 2014-03-31
forum: Hardware
---

### Post by rafal3 on 2014-03-31
Hi. I' new ubuntu user. Welcome. I have a problem with audio when I plug in my HDMI xable to my tv. I have a vido but no sound. The same problem was with Windows 7 and Windows 8.1. I contacted to MSI SUPPORT but the told me that there is a problem with drivers at the moment. In options I have HDMI CABLE NOT PLUGED IN. Is there any solutions for that?
Regards Rafal

---

### Post by trag on 2014-04-15
[COLOR=#000000][FONT=Ubuntubeta]download grub2customizer, under general settings change "quiet splash" to "quiet splash nvidia=audio1"or "quiet splash radeon=audio1" for some reason HDMI audio is disabled by default and must be activated via the kernal,using pavucontrol select Digital Stereo(HDMI)Output[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]good luck[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]trag[/FONT][/COLOR]

---

