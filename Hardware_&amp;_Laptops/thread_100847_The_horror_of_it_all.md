---
title: "The horror of it all"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by coderasm on 2005-12-08
Hello all.  I'm sad to say, I have damaged my Ubuntu install.  I'm running a gateway MX3560 and have Ubuntu Dual booting on it's own 20 gig partition.  I had it running perfectly, all my devices were working: sound, video and wireless.  I had wpa_supplicant installed and set to run at bootup using a script and symlink.  It was all working very well until I got the bright idea to try another wireless software other than wpa_supplicant.  I wanted to try out wifi-rader or gtkwifi, but first I had to disable wpa_supplicant.  This is where the trouble began.  To turn off wpa_supplicant, I ran the command sudo killall wpa_supplicant, and wpa_supplicant stopped running.  Then I tried running wifi-radar, but it just would not work, so I decided to reboot.  During the shutdown process I received hundreds of firmware errors relating to my ipw2200 module. The errors would not let the laptop shutdown, so I had to hold the power button down, something I always dread doing.  Then I rebooted.  It rebooted with no errors up to the point of the login screen, after I finish logging in, the whole system runs extremely slow, I have no wifi connection and running any application takes forever.  Where do I begin to fix this mess?  Should I just re-install over the partition? Thanks for any help.

---

### Post by Hobbes on 2005-12-08
You shouldn't have to reinstall over the whole partition.  Try running "top" in a terminal to see what is hogging all the cpu/memory.  Also you may want to uninstall your wpa_supplicant before trying to run the other one, or just in general if it is causing you problems.  Good luck and if you still have problems plz post the results of the "top" ie what is the system hanging on.

---

### Post by coderasm on 2005-12-08
Thanks for the advice Hobbs.  During my bootup, I just ctrl-c 'd through the network configuration.  Then I was no longer laggy when I was completely logged in.  Then I went into the package manager and completely removed wpasupplicant.  Also removed the wpasupplicant boot script from init.d.  Thanks for your help.  Now I'm on to gtkwifi.

---

