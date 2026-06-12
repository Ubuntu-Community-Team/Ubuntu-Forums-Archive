---
title: "Unknown display in Bionic"
date: 2018-04-14
forum: Hardware
---

### Post by mizurdiaga on 2018-04-14
I have just installed Bionic and I have some issues with the screen display. Settings -> Devices -> Screen display says that there are two displays (built in display and unknown display), while there is only one. My laptop has an integrated intel graphics card and a gforce gt540m. Moreover, I cannot see anything in the login screen (but I enter my pasword and I login correctly). Any suggestions? I have installed nvidia-driver-390 from Additional Drivers.

---

### Post by rbmorse on 2018-04-14
I had the same experience.  

Select the nouveau driver in "additional driver" wizard, then reboot the machine. Once you're back up, remove any packages related to the 390 driver from the installation.  When finished (re)install the 390-driver metapackage from the package repository...don't use the "additional driver" wizard.  Reboot again and you should come up on the proprietary 390.43 driver.

---

### Post by mizurdiaga on 2018-04-16
Thaks! It worked fine. But I needn't to install again the nvidia-390 driver, since removing all packages related to this driver fixed the problem.

---

