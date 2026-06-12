---
title: "circular scroll in jaunty"
date: 2009-05-05
forum: Hardware
---

### Post by theboytony on 2009-05-05
I have upgraded to jaunty and would like to get circular scrolling working on my touchpad, I found a guide but it says to add the following 2 lines to xorg.conf

Option "CircularScrolling" "on"
Option "CircScrollTrigger" "2"

but in xorg.conf all the parts for the synaptics touchpad are commented out and the line above the section says

# commented out by update-manager, HAL is now used

I uncommented the section and added the lines but it didn't work

Can anyone tell me what to do next please

Thanks

---

### Post by Altay_H on 2009-05-05
There are generally two ways to solve problems; the easy way and the sleek way. Here's the easy way:

Follow the instruction on the fourth post in this thread:
[http://ubuntuforums.org/showthread.php?t=979533](http://ubuntuforums.org/showthread.php?t=979533)


The "short guide" linked to in the post is written for 8.10, but I can confirm that it works in 9.04. Let me know if you have any trouble.

---

### Post by theboytony on 2009-05-06
thanks I got it working but not properly, if i make to small a circle it scrolls up and down, if you think of it like a clock when i go from 3oclock to 9oclock it scrolls down then from 9oclock to 3oclock it goes up, to make it work properly i have to make a circle the size of the touchpad do you know if this can be chnged

Thanks for everything so far

---

### Post by Altay_H on 2009-05-06
> **theboytony said:**
> if i make to small a circle it scrolls up and down, if you think of it like a clock when i go from 3oclock to 9oclock it scrolls down then from 9oclock to 3oclock it goes up, to make it work properly i have to make a circle the size of the touchpad do you know if this can be chnged

I had trouble with this until I realized how it was implemented. Unfortunately the circular scrolling is based on the location of your finger relative to the center of the touchpad, not based on where your finger was last located.

What this means is that you must always make circles around the center of the touchpad regardless of their size. You can make small circles around the center if you like, which is generally what I end up doing. It's not as natural as other implementations, but it works once you get the hang of it.

---

