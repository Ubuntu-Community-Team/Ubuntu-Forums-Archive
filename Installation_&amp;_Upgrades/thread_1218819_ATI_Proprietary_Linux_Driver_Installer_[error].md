---
title: "ATI Proprietary Linux Driver Installer [error]"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by dogafin on 2009-07-21
hi, just a couple days ago my computer quit playing sounds, (i have no sound). so i did a fresh install of ubuntu intrepid via cd and updated to the latest version (jaunty) and start from scratch in hopes of fixing the problem. but after getting situated with the fresh install, i noticed i still have no sound.

did a hardware driver scan, and nothing shows up in the list. nada. empty.. i remember going thru this route to get compiz working and install the ati driver, but this time i see nothing on the list.

so ive installed the driver, and followed instructions.. and this is what i got from the terminal:

> dogafin@dogafin-desktop:~$ su
Password: 
root@dogafin-desktop:/home/dogafin# '/home/dogafin/Desktop/ATI/ati-driver-installer-9-3-x86.x86_64.run' 
Created directory fglrx-install.SmaKiv
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593
......................................................
......................................................
......................................................
......................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-13-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.SmaKiv
root@dogafin-desktop:/home/dogafin# 



im trying to install the driver as per instructions here: [http://www2.ati.com/drivers/linux/linux_8.16.20.html#176980]("http://www2.ati.com/drivers/linux/linux_8.16.20.html#176980")

can someone tell me how to fix/set by --iscurrentdistro or whatever that is.. if thats what i need to do to install the driver. i really want my sound working on my pc again.

thanks in advance!

p.s.
idk if this helps but my ALSA information is located at [http://www.alsa-project.org/db/?f=92ed133cca577150e3f2061112318c83633cdde5]("http://www.alsa-project.org/db/?f=92ed133cca577150e3f2061112318c83633cdde5")

---

### Post by Mark Phelps on 2009-07-21
The ATI driver is for video, not sound.  IF you're getting no sound, installing this driver won't help.  What make & model is your video card?

---

### Post by dogafin on 2009-07-21
Thank you for your response. i thought Ati handled audio too, my hardware is ATI Radeon&#8482; Xpress 200 with Intel celeron. (i prefered machines with amd, so i was partly blaming intel lol). it seems that my problem is nothing but wiring issues.

i did more investigation and stumbled across this thread [http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/]("http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/")
on the article, it asked:
(1) Go to a shell and type:
Code:
> aplay -l
and i got:
> dogafin@dogafin-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dogafin@dogafin-desktop:~$ 

and oddly this message indicates that i have a working hardware or it wouldve said
> aplay: device_list:221: no soundcard found...
so...

i tried to check my peripherals and with luck, found that i have just a loose connection. something i doubted since none of my wires have been moved, and besides ive checked it before, secondary to checking if i have things muted. so i went ahead plugged/unplugged everything to see if i get any sound. i noticed that my s-video/audio cable on my sony subwoofer was kind of jimmyin a bit and that was the problem! i checked all connections but that! and ive missed it! im going to have to take a closer look since it is now very sensitive and my audio keeps going out. it doesnt feel like a tight fit anymore so i may have broken something.

again thank you for your time! and i apologize for the inconvenience!

---

