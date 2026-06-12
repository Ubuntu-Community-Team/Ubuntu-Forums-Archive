---
title: "T42 graphic driver"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by batnas on 2009-08-13
Hey all

I have a T42 with a ATI Radeon 7500 graphic card.
My goal is to run Diablo 2 on wine, anyway....
I tried to install fglrx, but that completely fu**ed up.
I followed the guide here:
[http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/#video]("http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/#video")
All went fine, until i tried to reboot it:(
When i boot now it comes to where to login screen should be, then the screen just shows some colors(don't know how to explain it):confused:

What am i going to do??

I have tried to run the Live-CD and it works.
I have tried to changethe files i should change in the guide. Didn't work
I dont know what to do

Please help me

\\Batnas

---

### Post by Mark Phelps on 2009-08-14
You didn't mention the Ubuntu version you're running (or I didn't see it in your post).  IF it's 9.04, and you would have searched these forums before you forced that install of fglrx, you would have discovered that there is no working fglrx driver for your card under Ubuntu 9.04.  The liveCD works because it installs the open source driver -- which does work.  But that driver does not provide 3D acceleration needed for decent frame rates for gaming.

So, basically, you can't do any serious gaming with Wine under 9.04 with that card.

You will need to remove the fglrx driver and install the open source driver.

If you're running 8.10 or earlier, my previous comments don't apply and it then could be a Wine-related problem.

---

### Post by Yellow Pasque on 2009-08-14
Do this (boot to recovery mode or use Ctrl+Alt+F1 to get to a terminal):
```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```
Reboot and all will be well.

---

