---
title: "Gaming Hardware Problems (Diablo 3)"
date: 2013-01-22
forum: Hardware
---

### Post by jayzon915 on 2013-01-22
I hope this is in the right place. I will try to be brief. 

I have a older gaming machine that was running Windows 7 and able to play Diablo 3 flawlessly on high settings. I really want to switch over to Ubuntu and learn more about Linux. However, the only thing that is holding me back is Diablo 3 performance.

I've been playing with it for a couple weeks now and am stumped. I was having some other issues with a wireless card Linksys AE1000  (RT3572) freezing the system. I read has trouble with sleep mode so I switched to a different card that seems to be working. Now I am trying, in vain I feel like, to get the video card performing close to it's Windows 7 performance. I have Diablo 3 installed using WINE and PlayonLinux separately but both installs lag significantly in game. 

SPECS:
AMD Phenom II x4 3.5Ghz
8GB DDR3 
2 500GB SATA 3 7200RPM HDs in RAID0
Asus M4A88t Motherboard
PNY GeForce GTS 250 1GB
     - Running 'glxgears -fullscreen' I average ~3300 fps
     - Running 'glxgears' I average ~23000fps
     - nvidia driver version - 304.51
     - Using NVIDIA Binary Xorg driver from nvidia-current

Things I have tried:
Installed Ubuntu 12.10
Switched from Unity to 'Gnome-Session-Fallback' because Unity has a negative impact on gaming performance. 
Using Nvidia binary Xorg drivers instead of the Nouveau display drivers because I have told that they have better performance. 
Upgraded the OS fully, 'apt-get upgrade' and believe that everything is updated and stable. 
Using PlayOnLinux v4.1.8 and Wine 1.5.5 patched for Diablo 3.
Tried setting the Affinity to both a single core and two cores within WINE with performance getting worse.

At the lowest possible resolution with all of the graphics set to low/off the game jumps 10-40fps constantly even when standing still. When I get in game the fps still drops and jumps like crazy and is unplayable at any resolution. I don't feel that it is a problem with PlayOnLinux or WINE as I have checked everything against other setups that work.

Any advice on things to check/fix within Ubuntu?

---

### Post by jayzon915 on 2013-01-22
I meant to post this in Gaming.... Not sure how to delete it so I marked it as Solved. Thanks

---

