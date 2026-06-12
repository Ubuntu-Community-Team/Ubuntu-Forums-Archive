---
title: "Only 800x600 with ATI card"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by Famished on 2009-03-25
I've just loaded 8:10 as boot option on a box with this card:-

Name    ATI 3D RAGE LT PRO
PNP Device ID    PCI\VEN_1002&DEV_4C42&SUBSYS_00000000&REV_DC\4&618BA55&0&0008
Adapter Type    ATI 3D RAGE LT PRO AGP 2X (A2U2), ATI Technologies, Inc. compatible
Adapter Description    ATI 3D RAGE LT PRO

I have a 22" Dell monitor and, in Windows XP, this card will run at 1600x1200 - if I wanted to !     But, in Ubuntu, I can only get 800x600.   In the Monitor Screen app I get a pink Unknown.   And this limit is confirmed by

famished@Wilfred:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

How do I empower the card and/or monitor?

---

### Post by Mark Phelps on 2009-03-25
You can experiment with the monitors and options in the screen resolution applet and see if you can find a combination that will give you more than 800x600.

You can try manually adding a modeline, or more modes, to your xorg.conf file to see if they get recognized.

But if neither of those work, unless you can get proprietary drivers from ATI for your card, you're limited to 800x600.

---

