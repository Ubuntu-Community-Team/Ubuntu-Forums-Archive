---
title: "Quick Check: Proper Method for Video Card Upgrade"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Battie on 2007-11-26
Hello.

I am about to upgrade my video card and have never done so on a Linux box.  Both cards are NVidia, so do I need to remove the NVidia driver before swapping cards, or does it figure everything out by itself?

Thanks!

---

### Post by mysticrider92 on 2007-11-26
You will probably not need to reinstall the nVidia driver, as long as the current one supports the new video card (nVidia has a compatability list on their website). 

While I have never actually done this, I think that with the driver setup on Linux, it should be plug and play. 

Just to make sure, what card are you putting in, and what is the current card?

---

### Post by Battie on 2007-11-26
I'm going from a 7300 GS to and 8400 GS, which according to NVidia's site (thanks for the reminder!) is supported.

I guess I won't really hurt anything even if the driver does freak out, but that's really cool that you don't necessarily have to reinstall.  I'll let you know how it goes when I get to try it in a few hours!

---

### Post by mysticrider92 on 2007-11-26
The main reason I was saying that is the 8*** cards, with the exception of the 8800's are only supported by one of the latest drivers (the newest one, last time I checked). Ubuntu's .deb is for a slightly older driver, that does not support the 8400, 8600, and a few others. This might have been fixed in Gutsy, I don't know.

I had a problem getting our 8600GT to work with Gutsy, since only one driver would work, and it had to be installed manually. 

I would just install the card, and see what happens. If Ubuntu drops you to a terminal with an X error, type "sudo nano /etc/X11/xorg.conf". Scroll down on this file until you find 'driver    "nvidia" ' and changed nvidia to just nv. Save the file (Ctrl>O) and exit nano (Ctrl>X). Now type "startx" and you should be back into your desktop, and can solve the driver problem.

---

### Post by Battie on 2007-11-27
How odd... my post didn't go through last night...

Anyway, everything seems to work fine now.  I had to remove nvidia-glx and replace it with nvidia-glx-new, though.  The only weird part was when instead of X  crashing to a console when the old driver failed, the screen blanked.  Yay for recovery console?

Thanks for your help!

---

### Post by Battie on 2007-11-27
Ah, there is something off:

I've rebooted a few times to be sure, but it turns out that that screen-blanking thing isn't a crash, but is what happens when I should be seeing the startup splash-screen.  I reconfigured the X-server (why not?), but it made no difference.  I will poke around myself, but any suggestions would be appreciated.

---

