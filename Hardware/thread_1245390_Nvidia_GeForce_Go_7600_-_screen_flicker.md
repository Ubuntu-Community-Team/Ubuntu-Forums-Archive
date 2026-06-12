---
title: "Nvidia GeForce Go 7600 - screen flicker"
date: 2009-08-20
forum: Hardware
---

### Post by majestic0110 on 2009-08-20
Hi all, I hope you are well. I am very new to Ubuntu and I am experiencing occasional screen flickers (the monitor will go black for a split second, then resume as normal). Now, I have tried googling for a solution but I have not found one yet that satisfies the issue. As you can imagine, its rather headache inducing. My system is a Toshiba satellite pro p100 pspae. I have an nVidia Geforce go 7600 and I have installed the Nvidia  server setting utility and have driver 180.44. My distro is Ubuntu 9.04 (jaunty) GNOME 2.26.1. 
Things I have tried to do to rectify the flicker include : DISABLING "Force full GPU scaling". I also tried specifying a refresh rate of 60mhz resolution = 1440*900. Although everytime I apply this, the X utility reverts my preference here back to AUTO (only with the refresh rate and resolution: it remembers the disabled "Force full GPU scaling". Sorry about the long post, I am just trying to provide as much information as possible. Thanks for your time and I hope we can sort this together as it is giving my eyes some trouble!!

---

### Post by majestic0110 on 2009-08-21
Any thoughts on this ? Not been able to solve it myself, I'd be really grateful for any advice.

---

### Post by majestic0110 on 2009-08-31
No takers? lol. Still having this problem, I have searched high and low for a resolution without getting one. I have no idea how to fix this so any thoughts will be greatly appreciated!

---

### Post by majestic0110 on 2009-09-03
Hi folks, I seem to have found a fix for this, so I will post it here for anyone else experiencing these awful flickers. 
> 
gksudo "gedit /etc/modprobe.d/options"

edit etc/modprobe.d/options. I added :

options nvidia NVreg_RegistryDwords='PerfLevelSrc=0x2222'
options nvidia NVreg_Mobile=1

It was empty  before.This information was found at this URL [http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)

I hope this helps someone else! It seems to have fixed it for now, at least. It seems that this code is basically locking the GPU power scaling, which is to blame for the flicker. Does anyone know of any downside to this ? 

EDIT : this actually has not completely resolved the issue - it has improved it though - i.e. it now flickers less often. I am determined to get a proper fix for this though, it is most irritating!

---

### Post by Frantic_Earthling on 2009-11-05
> **majestic0110 said:**
> Hi folks, I seem to have found a fix for this, so I will post it here for anyone else experiencing these awful flickers. 
This information was found at this URL [http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)

I hope this helps someone else! It seems to have fixed it for now, at least. It seems that this code is basically locking the GPU power scaling, which is to blame for the flicker. Does anyone know of any downside to this ? 

EDIT : this actually has not completely resolved the issue - it has improved it though - i.e. it now flickers less often. I am determined to get a proper fix for this though, it is most irritating!

The above-mentioned fix did not solve the problem for me! (Asus M70NV with GeForce 9650M GT and Karmic).

---

### Post by garthos on 2012-10-12
Recently installed 12.04 and once installing nvidia proprietary drivers (version current) I also was plagued with the screen flicker issue. I tried the (post-release) as advised by another forum with the same results. 

I then found the solution was to set my refresh rate.
alt-f2 
gksudo nvidia-settings

X Server Display Configuration 

My monitor resolution is set here but the refresh rate was set to auto, I have changed to 60Hz and I'm back in business. FYI nvidia version 295.49, geForce 7600

---

