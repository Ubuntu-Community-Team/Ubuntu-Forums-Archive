---
title: "Best settings for better battery life and general use?"
date: 2012-03-10
forum: Hardware
---

### Post by ms0chez on 2012-03-10
Hey guys, new to ubuntu so I apologize now if I come off as a noob. 

Background:
Finally got Ubuntu 11.10 to install on my brand new laptop today after banging my head against the wall since 6:30 in the morning. Had to set nomodeset in order to boot it from a live cd(Guess its a driver issue with AMD proccessors? Correct me if I'm wrong cause I really want to better understand all this) Then it wouldn't boot after the install, tried several different methods all to find out after 2 reinstalls that it was still not reinstalling completely and not to do with a corrupted or scratch CD. It was my sorry Wifi. So reinstalled from a friend's house. Installed fully but still wouldn't boot but once I installed fglrx it finally booted for the first time. Updated repositories and got software up to date.

Bugs:
1. My touch pad is all finicky at boot and eventually stops working after 5 minutes 
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps (<--this command fixes that but still have to do it each boot)
2. 2 drivers are showing in Additional Drivers: "ATI/AMD Proprietary FGLRX graphic(post-release upgrades)" and "ATI/AMD Proprietary FGLRX graphic"The post-release upgrades driver won't install and when I try to install it uninstalls the other driver
3. Not so much of a bug, my settings might not be optimized right but battery life seems a worst than windows

Piece of Machinery:
Samsung NP305V5A-A04US

Main Question:
What are the best settings for my system for better battery life and all around performance? I noticed AMD Catalyst Control Center is also installed.

---

### Post by 2F4U on 2012-03-11
For battery management you should definitely take a look into TLP. This is basically a set of scripts and settings for power management and particularly useful on laptops. It has been developed with Ubuntu in mind.

[https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management](https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management)

---

### Post by siepo on 2012-03-11
The next release, 12.04, is already in beta and promises (much) better battery life. So you could just put up with bad battery life for now and hope that 12.04 fixes it.

Meanwhile, you can dim your display and turn off unused devices in the BIOS.

---

