---
title: "Stuck on 'Loading'"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by OctaneHugo on 2009-01-30
When I installed the newest stable Ubuntu onto my XP running computer, I rebooted. I chose Ubuntu from the boot menu, and the logo came up. The bar filled fairly quickly, and then "Loading" came up, followed by some text telling me to type "help" to see commands. Well, it seems to be stuck there - it responds tot yping in commands and such, but it never gets past "Loading, please wait". The files checked out OK and the CD is fine. Any help?

---

### Post by dstew on 2009-01-31
Boot again, choosing Recovery Mode. See if you can tell what the errors are before it drops to the busybox command line. That might give a clue to the problem.

---

### Post by OctaneHugo on 2009-01-31
With ACPI workarounds, only thing I could catch was "MSI Quirk Detected". In Safe Graphic mode, I got the same thing. In Verbose mode, I got it again.

---

### Post by OctaneHugo on 2009-02-03
No help? I was planning to try another disc and re-download, but I'd like something else to try too.

---

### Post by dstew on 2009-02-04
What computer do you have? Does the Live CD work correctly? Which version of Ubunut are you installing?

---

### Post by OctaneHugo on 2009-02-05
I have a 3 year old eMachine (yes, I know it sucks). I'm trying to install 8.10

---

### Post by dstew on 2009-02-06
I could not find a definite solution. My suggestion: try an earlier distribution, like 8.04. That might work. Sometimes older kernels work better on older hardware (and new hardware too!)

---

### Post by OctaneHugo on 2009-02-08
I put 7.10 on a disc. If I select "Install in text mode", I get
"PCI: Cannot allocate resource of Region 3".
Then it goes into the installation process - scanning the CD and such. I go ahead ans elect Guided Partitioning for the entire disk, and it goes through that. I enter the info for the user accounts, and then it starts installing the base system. Then it configures the apt. Goes through select and install software.

It finishes the installation and ejects the CD, saying that it needs to reboot. I take the CD out and let it reboot. It gets to a screen with "Ubuntu" and a loading the bar. The loading bar fills up, and then the monitor shuts off. The tower is on, the mouse and speakers are on, and the keyboard is off. The monitor acts as though the computer is off - if you restart the monitor it says the monitor is working, and that the computer is off. Help?

---

### Post by dstew on 2009-02-10
Probably a graphics card that is not working well with the Ubuntu system. Try booting the system in Recovery mode. For 7.10, you can correct graphics system misconfigurations from recovery mode using the command```
sudo dpkg-reconfigure xserver-xorg
```After you finish with the command, you can reboot with the command```
sudo shutdown -r now
```Or, you can just try to restart the xserver with ```
startx
```

---

### Post by OctaneHugo on 2009-02-10
When it was starting up in recovery mode, I saw "PCI: MSI quirk detected. MSI deactivated." I'm still getting the region 3 error, and it's still having the monitor-keyboard problem.

EDIT: New development. Instead of turning off the computer after the monitor shuts off, I let it stay. After a few minutes, a dialog box popped up, saying the monitor was on the wrong frequency. Then it shut off again. But then, a few minutes later, I heard bongo drums. Very loudly. I'm guessing the monitor isn't compatible, and I'm not sure how I'd get drivers (if there even are any) installed.

---

### Post by dstew on 2009-02-11
Again, if you are using 7.10, you should try to reconfigure your xserver, as I posted above. When you get to the section about choosing a driver, select **vesa**. When selecting the "highest resolution", pick the resolution you actually want to use. That should get you a working desktop. Later, you can configure it more exactly. You can try the GUI tool displayconfig-gtk to select your exact monitor once you have a desktop working. To do that, from a desktop, press alt-F2, and enter```
gksudo displayconfig-gtk
```on the command line.

---

