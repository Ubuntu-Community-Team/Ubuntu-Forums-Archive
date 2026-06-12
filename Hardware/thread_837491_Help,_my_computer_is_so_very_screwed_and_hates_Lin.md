---
title: "Help, my computer is so very screwed and hates Linux"
date: 2008-06-22
forum: Hardware
---

### Post by Fzang on 2008-06-22
No matter which live CD I try or how many times I try it, it just won't boot...

The problem is something called ACPI I believe... not sure what it is because I'm fairly new to linux.

At one point I managed to install Mandriva completely from the CD which actually worked this once... however Mandriva wouldn't boot after install, only Windows would....

If I turn off this so called "ACPI" all live CDs boot just fine... but then my wireless network dies. The network is a typical laptop on/off WLAN switch. To turn the network on again, I have to boot windows, flip the switch and wait like 10 seconds!

When I turn off ACPI I can use the live CD but without any network, which really sucks because that's the only way I can access the internet at home and school....

Some distros doesn't say anything, some say the firmware is missing or something..

This is really ticking me off.... WHAT DO I HAVE TO DO!?

:( Stupid laptop... probably the most linux-incompatible thing sold

---

### Post by Fzang on 2008-06-22
Bump...

Dammit, I hate my computer but I got it for school and not for messing around with, so there's no way I can get another..

Any heeeeelp out there?

---

### Post by bubba_169 on 2008-06-22
Do you know what wireless network hardware you have? You can use windows device manager to find this. You probably need to find the drivers or use ndiswrapper to get that working with linux! When you find what model you have just search google for 'InsertYourWirelessCardNameHere on linux' and you'll likely find tutorials on how to get it working! 

ACPI is power management. Older computers might use something called APM instead of ACPI which basically does the same job but in a different way...

---

### Post by Fzang on 2008-06-23
So, how do I do this? Disable ACPI then try to enable wireless with ndiswrapper inside the linux?

My problem isn't incompatible drivers, because they used to work just fine on the live CD of mandriva, but somehow it all messed up and now I can't boot live CDs or install a bootable linux

:(

What happened?

---

