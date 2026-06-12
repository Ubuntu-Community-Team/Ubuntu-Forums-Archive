---
title: "Printer Problem"
date: 2012-11-16
forum: Hardware
---

### Post by mentisafer on 2012-11-16
Hi, I have a problem in Lubuntu with a new printer a just bought. I tried to set it up and couldn't make it to work. 
Brand new, HP Deskjet 1000 Printer J110 Series.
According to documentation on Ubuntu website, this printer is compatible, so I followed instructions on link, had to download HPLIP, latest version (hplip-3.12.10a.run) to Desktop, and then on terminal cd to Desktop, then run this command: 
'sh hplip-3.12.10a.run'
I followed the instructions, there was a dependency problem that since I chose automatic install on terminal I was able to solve but had to choose software for Ubuntu 12.04 since 12.10 (i got Lubuntu 12.10) isn't supported, so I just typed 'y' for yes to this suggestion. 
Then a GUI software came up where I just finished install, requested restart since I had the printer plugged in through USB cable, and then finally I run command:
'hp-setup' and though I have the software it doesn't print anything, this is what I the terminal gave:

QGtkStyle was unable to detect the current GTK+ theme.
Searching... (bus=usb, search=(None), desc=0)
\WARNING: gnome-keyring:: couldn't connect to: /run/user/kaliman/keyring-m8clIX/pkcs11: No such file or directory
WARNING: gnome-keyring:: couldn't connect to: /run/user/kaliman/keyring-m8clIX/pkcs11: No such file or directory

Please help, I need to get the printer to work.

---

### Post by rudregues on 2012-11-17
It seems an old bug titled 
"[SIZE=2]XFCE  (and other non-GNOME) desktops do not initialise gnome-keyring  correctly / WARNING: gnome-keyring:: couldn't connect to PKCS11[/SIZE]"
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177)
 
Use an Ubuntu Live-CD to install the drivers and test the printer, if this works install it as a temporarily solution to get the printer working until developers correct this bug.

  [ ]'s

---

### Post by mentisafer on 2012-11-18
thanks! i just installed Ubuntu and it worked right away, I dint even need to set up anything, great.

---

