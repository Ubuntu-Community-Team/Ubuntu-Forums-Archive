---
title: "Cannot log in after 9.10 upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2009-10-31
I just completed the 9.10 upgrade. Everything apparently went just fine and I rebooted when instructed to do so. All of the bootup screens looked normal until it presented a desktop-login: prompt on a text screen that was flickering, very badly. It took me many keystrokes to be able to enter my three-character login id. I was never able to successfully enter my 9-character password, as the characters are not echoed to the display.

So, I shut down the PC, waited a minute, and powered it back up. The same thing happened, again. I need help, please.

Tim

---

### Post by ratcheer on 2009-10-31
Ok, I have my PC booted into GUI mode after booting in recovery mode and editing /etc/X11/xorg.conf, changing Driver = "nvidia" to Driver = "nv". I saw this in another thread, and it worked.

However, it is still not using the nVidia driver. How do I properly install the nVidia driver for 9.10 without getting it all fouled up, again. I seem to have the understanding that, with 9.10, I am no longer supposed to download the proprietart driver from nVidia's website and install it myself. What am I supposed to do, instead?

Thanks,
Tim

---

### Post by ratcheer on 2009-10-31
Ok, I have the video driver all fixed. I downloaded 190.42 from nVidia and installed it in the usual manner.

Tim

---

