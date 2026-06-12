---
title: "Acer V3-771G-6851 Nvidia Optimus / Boot Problems"
date: 2013-01-09
forum: Hardware
---

### Post by kreppnar on 2013-01-09
OK, i just got this laptop a few days ago. It came with windows 8 pro 64bit. I went into bios and disabled the UEFI and tried to install linux. I have been trying a few distros but the one ive been trying the most is ubuntu. This laptop has Nvidia Optimus integrated. It has an Intel HD 4000, and a Nvidia GT 640M 2gig video card. So from what i have been able to do so far, is before i boot i have to do a nomodeset, in the boot command line. This gets me to the desktop. After i install it, i have to keep doing nomodeset everytime i want to start ubuntu. If i dont, it starts loading, and my screen completely shuts off. The hdd light stops blinking like it's finished loading, but the screen never turns back on. 

 So i have researched into the bumblebee-project, and installed it with help through the forums, and instructions page, and ive seen both cards work with optirun glxspheres. The thing is, even after installing bumblebee-nvidia, i still have to boot the computer with nomodeset, or the screen shuts off. This causes a problem when i go to logout of my desktop or press Alt + Ctrl + F2. I get a pure white screen, and i cant go back to my desktop, i need to hold the power button down and turn off the computer and reboot it. 

 So im here to find help on what is causing my laptop to black screen during boot, and how would i go around not having to put it into nomodeset? If i could get around this black screen error, everything would be fine.

Would there be any way to disable the intel onboard graphics driver and just use the Nvidia card with the normal nvidia-current drivers? Ive checked in bios to see if i could turn the onboard off there, but no luck on that one. Im not worried about saving power on this laptop. Normally when i use it, it's always plugged in.

Any suggestions? i would really appreciate it!

Thank you!

-Kreppnar-

---

### Post by kreppnar on 2013-01-09
ok so i have added i915.modeset=0 to my grub file. It starts up with no problem now, but i still cant logout or press Ctrl + Alt + F2 without having a solid white screen, and having to restart.

-Kreppnar-

---

### Post by kreppnar on 2013-01-10
Latest update. Found out that adding acpi=off to the grub line worked. Since having that option added at all times can be damaging to your system due to fan shut off. I added acpi_osi=Linux and acpi_backlight=vendor. It's all working like a charm. I can logout, and press Ctrl + Alt + F2 and go back and fourth between terminal and my desktop with no problems

-Kreppnar-

 Hope this clears up anyone else who has had this problem

PS: when acpi=off is enabled... bbswitch-dkm will not work for bumblebee. you will just get an error that says "Cannot enable Secondary GPU" and it will say "bbswitch is not found"

---

### Post by kreppnar on 2013-01-20
I have an entire How-TO install Linux Mint 14 and install Nvidia Optimus support on my blog. orkultus.wordpress.com

Hope this helps anyone with the same questions

---

### Post by cosmogoblin on 2013-02-24
> it starts loading, and my screen completely shuts off. The  hdd light stops blinking like it's finished loading, but the screen  never turns back onThis isn't the problem you think it is!  The screen is black because the brightness is set to zero.  You can do one of two very simple things:

[LIST]
[*]Increase the brightness with Fn + right arrow key
[/LIST]

[LIST]
[*]Just log in blind; username, enter, password, enter.  The screen's brightness will set to normal a few seconds later.
[/LIST]
This worked for me on an Aspire V3 771G  (not sure of the exact model).  Took me a while to figure it out, though.

---

### Post by ManfredU on 2013-05-15
> **cosmogoblin said:**
> This isn't the problem you think it is!  The screen is black because the brightness is set to zero.  You can do one of two very simple things:

[LIST]
[*]Increase the brightness with Fn + right arrow key
[/LIST]

[LIST]
[*]Just log in blind; username, enter, password, enter.  The screen's brightness will set to normal a few seconds later.
[/LIST]
This worked for me on an Aspire V3 771G  (not sure of the exact model).  Took me a while to figure it out, though.

Cool, works for me as well, thanks!

---

