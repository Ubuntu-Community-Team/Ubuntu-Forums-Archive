---
title: "wifi broadcom bcm4312 802.11b/g"
date: 2010-01-19
forum: Hardware
---

### Post by IKhider on 2010-01-19
Hello All, 

I recently re-installed Ubuntu after a 2 year hiatus. I have the above mentioned wifi card for my HP Pavillion laptop. What do I install to get it working?

Thanks!

-I-

---

### Post by cenzorrll on 2010-01-19
the "Hardware Drivers" application in your Administration menu should automatically find it for you.  if not the package is b43-fwcutter i believe. (do a search in synaptic for "broadcom" and you should see it)

if not then you may have to use the STA driver (also found in the repositories) but i think only wireless-n cards use that one.

if you do end up needing the STA driver, then i would highly recommend installing wicd and using that instead of NetworkManager, as you won't be able to get your max speeds for some reason, and constant disconnects have been a problem for me (don't know why, just happens)

---

### Post by Greenwidth on 2010-01-19
See:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by IKhider on 2010-01-21
Hello both and thanks for the post. I followed the instructions EXACTLY and the Wifi still does not work. And yes I did reboot the laptop and check for wireless networks, and so far--nothing. However, the blue light on my machine did go on. So at least that works. Now all I need it to do is detect wireless signals...

---

### Post by IKhider on 2010-01-23
Hello, if anyone is out there reading, 

I have a Wifi blue light on my laptop and I used both Wicd and Wicd-curses and no wireless signals are being detected. Could there be something interfering with the software you think?

In my home, there are loads of Wifi signals about, but my puter is just not picking them up...

---

### Post by Ayuthia on 2010-01-23
> **IKhider said:**
> Hello, if anyone is out there reading, 

I have a Wifi blue light on my laptop and I used both Wicd and Wicd-curses and no wireless signals are being detected. Could there be something interfering with the software you think?

In my home, there are loads of Wifi signals about, but my puter is just not picking them up...

Have you checked lsmod to see if the ssb or b43 module is loaded:
```
lsmod|grep -e ssb -e b4 -e wl
```
I don't recall HP using the Broadcom 44xx series wired network card so you should not need to have the ssb module or the b43/b44 modules.  

You can always try:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If it produces wireless sites, then most likely the ssb and/or the b43/b44 modules are loaded.  If it does not work, you can always reboot and you will be where you are currently.

---

