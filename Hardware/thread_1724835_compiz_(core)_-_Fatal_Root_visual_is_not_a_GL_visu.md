---
title: "compiz (core) - Fatal: Root visual is not a GL visual"
date: 2011-04-08
forum: Hardware
---

### Post by jwiddy on 2011-04-08
Hello,

Getting the following errors.  It's a 64bit laptop that was preinstalled with windows 7, but I had to roll back to XP and I'm dual booting Ubuntu 10.10.  

desktop effects could not be enabled

compiz
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Thanks for any help in advance,

Jeff

---

### Post by jwiddy on 2011-04-08
Found this compiz check program: 

./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G98M [GeForce G105M] (rev a2)
 Driver in use:         nouveau
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by Yellow Pasque on 2011-04-08
You're using open-source nvidia drivers (aka nouveau), and the ones included with Maverick aren't current enough to support 3D on your card. Either install nvidia binary driver or update your kernel/graphics stack: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by jwiddy on 2011-04-08
Not positive how do complete your recommendations.  

Also, I wasn't getting the "desktop effects could not be enabled"  error the first time I installed ubuntu.  (this is the 2nd time I've installed ubuntu)  Trying to figure out what changed.

---

### Post by Yellow Pasque on 2011-04-08
The easiest way is to go to System -> Administration -> Hardware Drivers and install the nvidia proprietary driver.

---

### Post by jwiddy on 2011-04-13
This is what I ended up doing and it worked for me.  Installed a fresh copy of ubuntu 10.10 64bit edition.

installed compiz from link below
[http://www.beakkon.com/geek/10-best-applications-for-ubuntu-10.10](http://www.beakkon.com/geek/10-best-applications-for-ubuntu-10.10)

sudo apt-get install simple-ccsm compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins emerald 

Did smart update via command line
[http://ubuntuforums.org/showthread.php?t=11103](http://ubuntuforums.org/showthread.php?t=11103)
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by curmudgeon38 on 2012-03-12
I have the same problem. Could you guys please give some more information? Do you know what the error means? So do you mean it is a problem with the driver?

I did apt-get install fglrx fglrx-amdcccle for my ATI driver, but I don't see anything in the proprietary driver menu.

---

