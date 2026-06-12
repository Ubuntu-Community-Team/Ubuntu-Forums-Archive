---
title: "AMD APU with discrete GPU Problem"
date: 2012-08-28
forum: Hardware
---

### Post by Domovoi419 on 2012-08-28
My setup: AMD APU 3870k with discrete Radeon HD 6670 
My only monitor is hooked up to my Radeon6670 and I have the bios set for dual graphics mode so that when I am in Windows (for gaming) it will use the APU dual graphics mode.

I do not need the dual graphics mode in linux, I just need the kernel to detect that the Radeon 6670 is my primary card.

This is the problem: When I install ubuntu 12.04 the screen goes blank for a second while the ubuntu loading screen is up and once X loads the screen comes back on and I can install normally.

When I boot up ubuntu 12.04 the screen goes blank when ubuntu loading screen comes up and then ubuntu loads normally with X but I can not access the console (alt f1-f6) just a black screen until i go back to x.

I have tried the additional drivers as well as downloading the latest catalyst drivers. Also I have tried adding nomodeset to the kernel line , which allowed me to see the ubuntu loading screen but still no console.

I have also tried adding fbcon=map:1 which I found in the arch wiki (link below) This is all I can find that is similar to my problem

[https://wiki.archlinux.org/index.php/ATI#Black_screen_and_no_console.2C_but_X_works_in_KMS](https://wiki.archlinux.org/index.php/ATI#Black_screen_and_no_console.2C_but_X_works_in_KMS)

---

### Post by Domovoi419 on 2012-08-30
My primary device in BIOS is set to PCI Express Graphics , Please read my bios configuration below as well as my problem further clarified, there is a link to a arch linux wiki page with a possible fix that does not work for me but this shows that others are having the problem   "  black screen and no console but X works" .

In ASUS BIOS under NB configuration:

IGFX Multi-Monitor - Enabled (I have this enabled to give me dual graphics option in windows for gaming.)

Primary Video Device: PCIE / PCI Video.     (The other option is for IGFX Video but this will push graphics to onboard apu )

Integrated Graphics is set to auto. .   (Other option is force)

HDMI dvi port output.   Set to auto

Pciex16-1/do port output.  Set to auto.



The reason I want my monitor hooked up to the discrete 6670 is because it is better than the APU as a primary for dual graphics for gaming. Also the AMD web page for dual graphics suggests the monitor hooked up to the better gpu (higer radeon number it says)  like I have it hooked up.

If I connect video to the onboard APU then it works for Linux and i can see tty console but It is not the right way to hook it up for dual graphics in windows and I get much lower frame rate in games if I hook it up this way. 

Also I wanted to clarify that under linux Xwindows works the only problem is no video at the ubuntu splash screen (no problem here as this is not important)  The main problem is once x loads and I see the desktop if I switch to the tty console with ctrl alt f1 - f6 it is a black screen , when I go back to X with ctrl alt f7 I see the ubuntu desktop again.

I would like the kernel to ignore the onboard graphics card when loading and only use the discrete card. I have tried the kernel modifier line suggestions of nomodeset and fbcon=map:1

fbcon=map:1 was actually suggested on a Arch Wiki page showing a possible fix to this exact problem , however it did not work for me,  Link is in the post above.

---

### Post by Domovoi419 on 2012-09-07
Just for a future note if anyone is searching for this problem and then reads this page.

I have contacted AMD about this issue and they have responded with the quote below.

"I have been able to reproduce this issue and generated an Engineering Problem Report against it. Our Linux developers will be looking at this issue. Please stand by." AMD Support

---

