---
title: "HP printer help - beginner level"
date: 2018-10-30
forum: Hardware
---

### Post by jmikul2 on 2018-10-30
Just upgraded to 18.04 for an older version.  HP Officejet 3830 worked fine before the upgrade as a USB.  Since upgrading all attempts to print fail.  Deleted and reinstalled multiple times, tried to set up with wifi.  System sees the printer but will not print.  I have had HPLIP 3.17.10 installed.  Command line skill are not good.  :(  Help!

---

### Post by Autodave on 2018-10-30
I rarely have any luck *upgrading* from one version to another.  I have always found it easier and quicker to just do a clean install.  IF you choose to do that, have your printer on and awake when you do the install. *Usually* the installer will see the printer (as long as it is an HP) and install everything without you having to do anything.  My wireless HP laser printer hooked up wirelessly w/o me having to do a thing when I installed 18.04.

---

### Post by dino99 on 2018-10-30
Do clean the system with: autoremove, gtkorphan, bleachbit (as root, carefully select settings)
This will remove old dependencies and settings that usually disturb the system.

---

### Post by ubu69 on 2018-10-30
I was having the same trouble (different printer and different setup) and did the autoremove step as suggested by dino99 in the above post (from the command line):

```
sudo apt-get autoremove --purge

```
Then, to be safe, I did an update and upgrade:

```
sudo apt-get update
sudo apt-get upgrade

```
And then rebooted:

```
sudo reboot

```
After the reboot, I was able to print a test page with no trouble.

---

