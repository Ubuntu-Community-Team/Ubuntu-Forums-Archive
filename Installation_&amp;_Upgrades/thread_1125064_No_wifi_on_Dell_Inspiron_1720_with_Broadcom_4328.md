---
title: "No wifi on Dell Inspiron 1720 with Broadcom 4328"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Jeffly777 on 2009-04-14
Just to head off the inevitable comments, I've spent the better part of two days and wasted a lot of good work time trying to get this thing fixed, and that includes searching on this site and others attempting myriad solutions which only led to varying levels of failure.

My situation is this:  This weekend I got sick of windows, and on a friend's recommendation installed Ubuntu 8.10 (Intrepid) on my laptop.  99% of everything went without a hitch--even my bluetooth mouse worked immediately and continues to work.  So it definitely works better than vista.

The problem I'm having is that I can't get my wifi to work, and that's a serious problem.  I have tried ndiswrapper with various broadcom drivers, and they would all say that the device was installed in the ndiswrapper gui, but would not show up when I ran iwconfig or anything else, and, needless to say, they didn't work.

I've also tried activating the Broadcom STA driver in the hardware drivers menu.  This led to my wired adapter not working.  My wireless seemed to be working, but it would not successfully connect.  Network manager would show me the list of available networks and try to connect, show the connection animation, get as far as "acquiring IP address," and then the network manager would say the connection was disconnected and I'd be without net until I plugged by ethernet in again.

I also tried running a few lines of code:

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan

These led to my wired adapter working and my wireless adapter seeming to work, but with the same inability to connect as before.  I know it's not the network--I've tried several and my other machines can connect without a hitch.  I've tried several different security configs from WPA and WEP to open.  I am running a MAC filter but the MAC address for this machine is listed in the allow list.

I'm out of ideas; if anyone can help I would really appreciate it.  My system is a Dell Inspiron 1720 with the Broadcom 4401 10/100 ethernet and the Broadcom 4328 wifi onboard.  I'm a total Linux noob, so I'm sorry if I left out useful information.

---

