---
title: "problems with update of linux-restricted-modules"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by erfahren on 2007-06-30
Since the last update of linux-restricted-modules (on 6/28/2007) I've had problems with X Window (I think that's what I'm having the problem with). Basically after resuming from screensaver/display sleep my screen is just comprised of white with little black dots, and my panels are all messed up. (Sorry I can't explain that better.) Also, my entire desktop will completely freeze periodically. Unfortunately I haven't been able to reproduce this intentionally. 

From my Synaptic history for 6/28/2007:

Upgraded the following packages:
linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) to 2.6.20.5-16.29
linux-restricted-modules-common (2.6.20.5-16.28) to 2.6.20.5-16.29
xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.5-16.28) to 7.1.0-8.34.8+2.6.20.5-16.29


My current fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)


I don't think its because of the fglrx driver update. Someone [here](http://ubuntuforums.org/showthread.php?t=488583) is experiencing a problem with the update as well but his xorg-driver-fglrx wasn't updated. 

I'm using a normal Gnome session. I've searched for anyone else experiencing problems with this but didn't come up with anything. 

It worked reasonably well before, how to I go about reverting to the previous version?

oh, I forgot --- my basic specs are below.

---

### Post by ROUBOS on 2007-07-01
Hi,
I don't know if this helps. I could not find help anywhere so I decided to try somethings out myself.

I tried re-installing fglrx drivers and xgl etc.

Then I went to ati.com and downloaed the ati-drivers. I first uninstalled previous drivers using their install instructions found here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.38.6-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.38.6-inst.html)

and then installed their drivers. 
I then enabled the Restricted drivers again and restarted. Problem solved.

I hope this helps.

---

