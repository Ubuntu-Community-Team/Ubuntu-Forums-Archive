---
title: "Can't login to Ubuntu on Compaq Presario 2105us"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by arohl74 on 2005-07-05
I am trying to use Ubuntu on the Compaq Presario 2105us.  When booting, I do get the login screen.  I enter my username and password but it freezes when the "Ubuntu" wallpaper comes up.  Any help would be greatly appreciated.

Allen

---

### Post by Xian on 2005-07-05
It sounds like some type of kernel line modifier needs to be used, but that is only a hunch based on similar experiences. Do a google search on "acpi=off" and see if the specs with users using this config seem to match your own. If so, you might want to look further. If not, I'd think you would want to look over your /etc/X11/xorg.conf file and make sure the specs listed for your monitor match those from your manufactuer.

---

### Post by arohl74 on 2005-07-05
Thank you for your response.  I booted into recovery mode and went into the /etc directory.  Unfortunately, there is no X11 directory.

I checked the xorg log in var and found the following:

using config file: "/etc/x11/xorg.conf" (even though the directory is not there).
   Server Layout "Default Layout"
   Screen "Default Screen" (0)
   Monitor: "Generic Monitor"
   Device: "ATI Technologies, Inc. Radeon Xpress 200M (RS480)
   
   The directory "/usr/lib/x11/fonts/cyrillic" does not exist
   The directory "/usr/lib/x11/fonts/CID" does not exist

The Device that was detected is correct.  I think the problem lies with the fonts.  Each time I've tried to install Ubuntu (or Kubuntu), there is an error loading the fonts.

What could be preventing the fonts from installing?

---

### Post by Jiilik on 2005-07-20
add Option "NoAccel" "true" in xorg.conf, or change the driver from ati to vesa.

---

### Post by Dr_Willis on 2005-07-23
Getting to be several related threads on this laptop. 

[http://ubuntuforums.org/showthread.php?t=45274](http://ubuntuforums.org/showthread.php?t=45274)  

is refering to some of your problems. Ive been spending most of the day checking all the threads and different sites gathering information.

---

