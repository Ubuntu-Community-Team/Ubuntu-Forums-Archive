---
title: "Ubuntu 10.4 alternate-  installer resolution issue"
date: 2010-05-01
forum: Hardware
---

### Post by NetBoy_Pilot on 2010-05-01
I am trying to install Ubuntu 10.4 Alternate on a Acer Aspire 3630, with a screen resolution of 1280x800.
 
When I start the installer (which is text mode), it shifts the laptop display down and writes the bottom information on the top of the display (also cutting off several lines).
 
If I hook up an external monitor (laptop LCD off), it behaves properly.
If I dual display both the externalmonitor and laptop LCD, the laptop display is shifted down and wrapped, and the external monitor has the left portion of text cut off. (seems like installer is defaulting to 1280x1024, the worst of both worlds)
 
I have got 10.4 to install, but now the boot loader (its encrypted) does not display properly. The place where I enter the password is cut off.
 
I have attempted to change the change the resolution of the installer by adding vga=640x400 to the startup line. When this fails, I select a resolution from the menu. Changing the resolution has no effect.
 
Anyone?? Please???
 
NetBoy

---

### Post by NetBoy_Pilot on 2010-05-04
I have done further testing and have gotten these results:
Insert Ubuntu 9.1 and boot laptop, press <Enter> for English, Press <F6> then hit <ESC> (to bring up additional options). At the END of the boot line, type
1) VGA=0x300 -> displays incorrectly [text shifted]
2) vga=0x300 -> displays CORRECTLY
3) vga=b -> displays incorrectly [text shifted]
4) vga=640x400x8, displays error, choose resolution, select 'b' or '0x300' -> displays CORRECTLY
 
When I try and the same on Ubuntu 10.04 LTS Alternate CD, I get:
5) vga=0x300 -> displays incorrectly [small colored boxes on screen]
6) vga=b -> displays incorrectly [text shifted]
7) vga=640x400x8, shows error, choose resolution, select 'b' or '0x300' -> displays incorrectly [small colored boxes on screen]
 
Is there anything else I should try?
 
-Net-

---

