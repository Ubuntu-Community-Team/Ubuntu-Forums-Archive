---
title: "Can't enable desktop effects (tried ati and nvidia)"
date: 2010-05-08
forum: Hardware
---

### Post by Envy Life on 2010-05-08
I have an ATI Radeon 9600 XT.  I installed Ubuntu 9.10, had occasional logout issues, where after using it the session simply terminates back to the login window.  No clue why, but also had odd issues where I could enable Compiz for one user but not for another.

So I did a clean install of 10.04, learned that ATI has dropped proprietary driver support for the 9600XT which makes me very concerned purchasing a new ATI card for future compatibility.  Unfortunately same issue.  I finally narrowed it down to the video card, got a 32MB Nvidia and it works great (well, can't enable compiz).  So I figure, let's get a new Nvidia with hardware support.  

I purchased a new Geforce 6200.  Works fine w/o compiz, but as soon as I enable any of the 3 Nvidia hardware drivers I get applications disappearing and logouts.  Same deal.

I verified that all 3 cards work perfectly fine with the standard/non-proprietary driver.  But apparently not possible to get Compiz on any of them.  I'm a long time Linux user, but am pretty darned close to putting Windows on that box... so if anyone has ANY ideas where to go from here, I'd be very grateful.

---

### Post by Envy Life on 2010-05-11
I figured my best chance is to continue to implement the newest Nvidia card, so I decided to purge all 3 versions of the NVidia hardware drivers to start fresh, because the only one specified to work with the 6-series is nvidia-current.  The specific versions of the binary driver available are 96, 173, and 195.36.15.

So I did that, then re-installed nvidia-current using System->Administration->Hardware Drivers.  I did a reboot or two just to make sure.  I could have sworn that I had the "current" driver specified as "Active and in use" but after exhibiting seg faults with Firefox, I checked again and it was listed as "Active but not in use".   The only option I have available to me is to click the "Remove" button or to reboot.  I rebooted and have the same situation.  In fact although I have nvidia-settings installed, I don't see it in the menu either.

Again, I'm very stuck.  This is my second clean install of 10.04, and what am I left with, to do another clean install and cross my fingers after all these failures?   Pretty terrible video driver support I'm seeing in this release.

---

### Post by Envy Life on 2010-05-11
I ran across this I'll have to check out in more depth.

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/105841](https://answers.launchpad.net/ubuntu/+source/xorg/+question/105841)

Mine reads     

Kernel driver in use: nouveau
Kernel modules: nvidia-current, nvidiafb, nouveau

---

