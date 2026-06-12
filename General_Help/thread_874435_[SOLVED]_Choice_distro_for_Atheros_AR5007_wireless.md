---
title: "[SOLVED] Choice distro for Atheros AR5007 wireless"
date: 2008-07-29
forum: General Help
---

### Post by DapperMe17 on 2008-07-29
Atheros AR5007 built-in wireless card...


Can anyone suggest a distro that has proven to allow "at-least" an unencrypted/open wireless connection out-of-the-box?

I have no problem working with madwifi or ndis to get the WPA going, however, I don't have access to a corded connection with this setup.

Thanks

---

### Post by kaffeboy on 2008-09-04
Yeah! I have Ubuntu, and after one month of non-stop tutorials and how-to's, it still doesn't work. I can manage to switch distros whenever, I just need to solve this problem by getting whatever distro it takes to make this work out of the box.

---

### Post by bodhi.zazen on 2008-09-04
[http://ubuntuforums.org/showthread.php?p=4790652](http://ubuntuforums.org/showthread.php?p=4790652)

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

---

### Post by IanW on 2008-09-04
Since going to kernel 2.6.27, Intrepid supports AR5007 on my EeePC 701 without any madwifi/ndiswrapper help.

This sounds wrong, but all I had to do was _turn off_ the driver in "System/Admin/Hardware Drivers" & reboot.

---

### Post by DapperMe17 on 2008-09-05
So,

Technically, does that mean that the "madwifi-hal..." patch for the ar5007eg(ar242x) is now included in the Intrepid kernel???

Meaning...no more re-compiling the "madwifi-hal..." patch after every kernel update?

Is WPA out-of-the box too?

---

### Post by DapperMe17 on 2008-09-25
Xubuntu 8.04 works great, with some compiling. See my other thread for the AR5007EG.

---

