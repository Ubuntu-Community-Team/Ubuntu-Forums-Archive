---
title: "Laptop display not being recognized as such"
date: 2008-08-04
forum: Hardware
---

### Post by Lappymode on 2008-08-04
Hi, well, I can't change the brightness of my laptop display, as it's not being recognized like it, whenever I try to move it lower, it tells me:

#~: xbacklight -set 50
No output have backlight property



Since I need this laptop for movility, and display is one huge powertaking device, I need to solve this...
I've tried searching through the schemes with gconf-editor, but it doesn't allow me to edit the schemes.
Only place where I've been able to find something similar is in a bugtrack and for MacBook users, however I tried the workaround, still it didn't work.

My graphic card is nVidia GeForce Go! 6150, running Hardy Heron.
In the same Laptop, I've got another partition with Debian running, where I actually can deal with brigthness, so I guess it's Ubuntu specific problem.

Can anybody point me in the right direction?

---

### Post by tuxxy on 2008-08-04
This may be useful

[http://linuxrevolutions.org/2008/05/14/ubuntu-804-laptop-screen-brightness/](http://linuxrevolutions.org/2008/05/14/ubuntu-804-laptop-screen-brightness/)

---

### Post by Lappymode on 2008-08-04
> **tuxxy said:**
> This may be useful

[http://linuxrevolutions.org/2008/05/14/ubuntu-804-laptop-screen-brightness/](http://linuxrevolutions.org/2008/05/14/ubuntu-804-laptop-screen-brightness/)

Thanks for the fast reply, still both solutions explained there didn't work at all.
Related mainly to the second script the diference with ATIM, where such thing does not exist in my system at all.
Tryied modifing it to set it to match mine, but still no effect.

Also, setting gamma lower does work, but I don't know how much of powersaving that is.
Edit: In order to give further info, under /proc/acpi, VIDEO does not exist in my system.
Second edit: the lacking of VIDEO is because of a tested workaround that didn't work (blacklisted VIDEO)
Still, it's not working.

---

### Post by philheaton on 2008-08-12
> **Lappymode said:**
> Thanks for the fast reply, still both solutions explained there didn't work at all.
Related mainly to the second script the diference with ATIM, where such thing does not exist in my system at all.
Tryied modifing it to set it to match mine, but still no effect.


ATIM is laptop dependent. you need to follow the path in Nautilus. You may find yours is something along the lines of /proc/acpi/video/VGA/LCD/brightness. Dig around in the /proc/acpi/video/ directory to find the exact match. 

You will more than likely need to alter the numeric values of the script to alter your brightness calibration. To find out what they are, you need to run "cat /proc/acpi/video/ATIM/LCD/brightness" from the terminal (without quotes), remembering to insert the exact path for your laptop. 

My script was altered to accommodate my particular laptop. The attached script may work better for you. Remember to follow the instructions (marked by a # within the script itself. Open it with a text editor to read them.)

Hope that works. 

As a side, the brightness issue seems to be being caused by the ACPI (Advanced Configuration Power Interface). If you boot the kernel with the acpi=off option, you regain control over the Fn keys and your screen brightness. This however is not a viable solution as you lose control over the other power saving features such as CPU frequency scaling. 

Cheers

Phil

---

### Post by Lappymode on 2008-08-12
Tried, but still whichever value I assing it from the ones that pops, do not work.
Either way I went back to Debian and I do not have this problem, so maybe the tittle should be set to solved.

---

