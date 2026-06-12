---
title: "Palm Tungsten T5 can't sync"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by ubuntuthinking on 2005-07-11
I have looked around but did not find any solid solution to syncing my T5 with gnome pilot or jpilot.  I have tried under SUSE 9.3 too with no luck.

Does anyone know of the current status of this issue or a workaround?  My T5 works well as a USB drive connected via USB - but I just can't get the sync to work
cheers,

---

### Post by mrcbrown on 2005-07-11
[QUOTE=ubuntuthinking]I have looked around but did not find any solid solution to syncing my T5 with gnome pilot or jpilot.  I have tried under SUSE 9.3 too with no luck.

Does anyone know of the current status of this issue or a workaround?  My T5 works well as a USB drive connected via USB - but I just can't get the sync to work
cheers,[/QUOTE]
 Have you gone through these steps?

[http://www.ubuntuguide.org/#configurepalmosdevices](http://www.ubuntuguide.org/#configurepalmosdevices)

---

### Post by ubuntuthinking on 2005-07-12
Yup - using "dmesg" I can see it connected to /dev/ttyUSB0 and ttyUSB1 after I press the hotsync button - but no luck with the rest of the configuration.  I have also tried pilot-xfer and get the same results.
 :???:

---

### Post by ubuntuthinking on 2005-07-13
bump

---

### Post by s_p_a_r_k_y on 2005-07-18
have you tried kpilot?

---

### Post by ubuntuthinking on 2005-07-18
Yes, thanks for the reply.  Kpilot, Jpilot etc all seem to have the same problem.  I have tried the udev modifications listed in the forums as well as on the ubuntuguide site.  

The issue seems to surround the lifedrive and T5.  Each of these devices reportedly shows up as two distinct usb connections at the same time.  It seems to work well as a USB drive, but I wonder if linux is confused by it showing up on USB0 and USB1 at the same time?

---

### Post by roastpork on 2005-07-18
What error messages are you receiving?

I am able to make my Treo600 sync with gpilotd/evolution after killing all instances of gpilotd and then starting gpilotd manually from command line with no arguments.  Just a stab in the dark?

-Mike

---

### Post by jochen on 2005-07-19
Not quite sure if Tungsten T5 is already supported by pilot-link. 
If at all then with the pilot-link-0.12 pre-releases. 

Have a look at [www.pilot-link.org](www.pilot-link.org)

Jochen

---

### Post by ubuntuthinking on 2005-07-27
Oops, 
sorry for the latent reply - I have had to switch back to XP whilst I take care of Flash programming and updates for my T5.  

In response:
1.  I don't get any errors that I can detect with regularity.  When using Kpilot, the sync begins, but then "hangs" and does not complete any task - I only have selected backup while getting this figured out.

2.  I will review pilot-link again to see what's up.

I won't forget this post - I really feel constrained by XP and miss Gnome.  Perhaps I'll try VMWARE while tring linux sync solutions.

cheers.

---

### Post by claudine on 2005-07-29
I'm using a T5, Warty and J-Pilot. I've had similar problems to yours, but I've found that if I press the Hotsync button on the cable just *before* pressing the Sync button on J-Pilot, the sync works fine. I'm using /dev/ttyUSB1.

---

### Post by robenroute on 2005-10-19
I've posted a possible solution to the sync problem:

[http://www.ubuntuforums.org/showthread.php?t=78918](http://www.ubuntuforums.org/showthread.php?t=78918)


Rob

---

