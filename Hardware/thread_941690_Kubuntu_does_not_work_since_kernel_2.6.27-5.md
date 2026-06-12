---
title: "Kubuntu does not work since kernel 2.6.27-5"
date: 2008-10-08
forum: Hardware
---

### Post by manoharanm on 2008-10-08
I'm a kubuntu noob and thought i'll check the forums for a solution.  I had installed the beta of Intrepid and using it for a few days now.   I had updated the kernel (and other items) that the update manager prompted me with, yesterday and Kubuntu wouldn't boot anymore.   It stops at the terminal prompt and the gui doesn't load.  I tried KDM start and get a message saying it is already started.   I tried startx and saw some issues with the RADEON driver (or something related to RADEON)

kinit: No resume image, doing normal boot...
stops at command prompt (terminal)
following error observed in the error log

(II) RADEONHD(0): Mapped IO at 0xb7abb000 
(II) RADEONHD(0): Mapped FB at 0xa7a4e000
Saw signal 11.  Server aborting.
kernel 2.6.27-6

Everything was running fine till kernel 2.6.27-4; error started with yesterday's update.  I rebuilt Kubuntu late yesterday using my ISO image (Intreprid beta) and everything was working okay until i thought i'll try my luck with the updates today.   Once upgraded, I see the same error today.

My config:
Gateway m6862 laptop
Intel Core2Duo T5750 2.0 GHz
4 GB RAM
ATI Mobility Radeon HD 2600
Dual boot with Vista

---

### Post by phidia on 2008-10-08
You are using a test release-you understand that right? Things are expected to break occasionally. You may want to read some of the threads in the [Development & Programming Forum]("http://ubuntuforums.org/forumdisplay.php?f=310") > [Intrepid Ibex]("http://ubuntuforums.org/forumdisplay.php?f=346") there have been recent reports there of problems with the xserver/xorg.

However you can try this command at the command line > fix X That doesn't work for me with the beta but you might have better luck.

---

### Post by manoharanm on 2008-10-08
Thanks Phidia.   I understand i'm using a beta and understand things may not work occasionally.   I just wanted to see if this was a known issue and if not, this might be a good time to report the issue. 
Thanks for pointing me to the other threads.  Reading them now...

---

