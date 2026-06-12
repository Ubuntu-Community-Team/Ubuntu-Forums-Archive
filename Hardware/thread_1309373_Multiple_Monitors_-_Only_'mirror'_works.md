---
title: "Multiple Monitors - Only 'mirror' works"
date: 2009-11-01
forum: Hardware
---

### Post by esgarrouth19 on 2009-11-01
I am on a Thinkpad R60 and using an LCD tv/monitor as my second screen. I can use the tv as a mirror of my laptop's screen, but I can't seem to set it as an extension of the laptop's screen. I was able to do this in 9.04 without a problem, but 9.10 isn't agreeing with the tv at all. Any suggestions? If you need more information, just let me know!

In case I didn't explain it well enough, I want to be able to display a website on the TV while I have an editor on my laptop (so nice for programming :D).

---

### Post by belgianfries on 2009-11-01
What graphics gard does the Thinkpad R60 have?

I had the same problem with 9.04 on a DELL desktop with an ATI card and eventually fixed it with the newest driver from ATI and configuring it with the standard display setup tool. The ATI setup tool ("Catalyst") failed.

Cheers,
Torsten

---

### Post by esgarrouth19 on 2009-11-01
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by belgianfries on 2009-11-01
So no ATI... I think a colleague has a notebook with Intel grapics and 9.10 - will ask him tomorrow about the issue and get back to you.

Torsten

---

### Post by esgarrouth19 on 2009-11-03
Any update? Or anyone else have any suggestions? :(

---

### Post by belgianfries on 2009-11-05
Sorry for getting back so late. I have asked the colleague but he as not tried a dual screen setup, so unfortunately I can't share any experience regarding that issue.

Would it be an option to use the 9.04 driver on 9.10 for now?

I am also wondering, if you can get it to work by enabling Xinerama?

Torsten

---

### Post by Kokopelli on 2009-11-05
Have you tried xrandr from the command line?  You are using Intel graphics.

---

### Post by drewlong on 2009-11-09
There are 2 packages that may be of interest, arandr and krandrtray, you get to them through the package manager. I am running Kubuntu and only arandr worked, I dont know why, krandrtray just brought up the standard display screen manager.

arandr opens up a small gui which then allows you to resize, position etc you then save the output in a file of your choosing. The output is an xrandr command line which you can then copy and paste, in my case to /etc/kde4/kdm/Xsetup, or simply add the file as a script to **System Settings -> Advanced -> Autostart** 

Please let me know if it works for you.  drewlong    :D

---

### Post by Yellow Pasque on 2009-11-09
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950#External_display_with_XRandR](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950#External_display_with_XRandR)

---

### Post by esgarrouth19 on 2009-11-10
Thanks for the replies! I've actually filed it as a bug and it has been confirmed. May not be fixed for a while, but at least they know about it now... I'll survive without a second monitor until then ;)

[Multiple monitors not supported on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/478859")

---

