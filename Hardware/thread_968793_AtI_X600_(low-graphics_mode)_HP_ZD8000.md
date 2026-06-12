---
title: "AtI X600 (low-graphics mode) HP ZD8000"
date: 2008-11-02
forum: Hardware
---

### Post by aarfritz on 2008-11-02
I have been trying for a while to get my video card working properly. I have a HP ZD8000 laptop with a ATI600 video card trying to run a 32inch Vizio VP322 as my main monitor. 

The problem is when trying to install the third-party drivers for the card, after the reboot it runs in low-graphics mode. But this is easily solved by disconnecting the Vizio and restarting. I can then run Ubuntu using the third-party driver using my laptop's monitor. Reconnecting the Vizio then restarting starts the whole process over again.

I have also tried installing the driver from the ATI website. During install i get:
Generating package: Ubuntu/hardysudo
E**rror: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions**
Removing temporary directory: fglrx-install.N20842


My version:

sudo uname -r
2.6.24-21-21-generic

I can use my Vizio with no problem without the third-party drivers, but it sucks. No Google Earth, lame. Hope someone is willing to help!

---

### Post by bjtuna on 2008-11-03
It looks like maybe there was a copy/paste problem there... try running the command exactly like this:

```

sh ati-driver-installer-8-10-x86.x86_64.run --buildpkg Ubuntu/hardy 

```

---

### Post by aarfritz on 2008-11-04
I have succesfully installed the driver from ATI's webstie, let me tell ya it was tons of fun! Anyways, now that I got it working I am running into another problem. When trying to run google earth, the system logs me out to the point where I have to enter my username and password. Kinda wierd. Im going to try to install google earth again just to see what happens. Any ideas?

---

### Post by aarfritz on 2008-11-04
Installing Google Earth again doeset work. Also, not that its a big deal, the advanced visal effects do not work. It tells me that the thrid-party drivers must be enabled. Didnt I do that when I installed the card?

---

