---
title: "X server won't play nice with new video card....."
date: 2009-01-30
forum: Hardware
---

### Post by whydoesitburn on 2009-01-30
I'm trying to upgrade my ATI all-in-wonder 8500dv to a nvidia 8400 gs, and every time I try to boot Ubuntu Hardy, the login screen will come up completely warped. I even tried running the live CD to see if it was because of my current configuration and the same thing happened after it got past the loading screen. 

I've read something in other articles about sudo dpkg reconfigure xserver-xorg not working under hardy like it does in other releases. I just reinstalled the ATI card, and Ubuntu loads up as it did before. Has anyone else experience similar problems when installing new video cards? 

Just tell me what system outputs I should post or articles i should read in order to solve this problem without reinstalling Ubuntu

---

### Post by taurus on 2009-01-30
When you have your ATI graphic card, did you install a driver for it from System -> Administration -> Hardware Drivers?  Before you replace your ATI with the nVidia, try switching the driver for your graphic card back to vesa (generic driver).  Then shutdown the computer and replace the ATI with nVidia.  Then reboot.  You might see a lower resolution so go into System -> Administration -> Hardware Drivers and install nvidia driver for your new graphic card.

---

### Post by cariboo on 2009-01-30
With the new video card i nstalled, start in recovery mode, and at the prompt type:

[CODE][sudo dpkg reconfigure -phigh xserver-xorg/CODE]

This will create a defualt /etc/X11/xorg.conf file. The reson you need to create a new /etc/X11/xorg.conf, is that the ATI driver is stil being loaded, that's why you are getting the wierd screen. Type exit at the prompt and continue loading to the desktop. Once at the desktop go to System-->Administration-->Hardware Drivers. Select the recommended restricted driver and let the program install it. Once the restricted driver has been installed, you will need to restart X you can do this by pressing Ctrl-Alt-Backspace, or reboot.

Jim

Edit: I guess I was to slow.

---

### Post by whydoesitburn on 2009-01-30
That did the job! Thanks for both of the replies!

---

