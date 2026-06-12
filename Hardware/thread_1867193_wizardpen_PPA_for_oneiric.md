---
title: "wizardpen PPA for oneiric?"
date: 2011-10-22
forum: Hardware
---

### Post by oriolfa on 2011-10-22
Hi,

I'm trying to use a Trust TB-5300 Tablet detected via lsusb as a UC-LOGIC Tablet WP8060U. The tablet used to work fine in Natty after installing wizardpen drivers via PPA ppa:doctormo/xorg-wizardpen

Now (after a fresh install of ubuntu oneiric since Alpha version) I'm not able to install the wizardpen driver, either via PPA (the PPA is not available for oneiric) or manually (dependencies broken).

I see there is a Wacom Tablet menu in the system properties, but it (obviously) does not detect UC-Logic tablets.

Any suggestion on how can I get my tablet working on oneiric?

Thanks in advance!
Oriol.

---

### Post by Favux on 2011-10-22
Hi Oriol,

Welcome to Ubuntu forums!

Until DoctorMO updates the PPA the question becomes does the WizardPen driver included in the Oneiric repositories work?

Check in Software Center if it is installed.  It should be called something like xserver-xorg-input-wizardpen.  If you can't get the Software Center to show you "technical" files then you'll have to install the Synaptic Package Manager and use it instead.  Once you've installed, or confirmed it is installed, the WizardPen X driver does it work after a reboot?

---

### Post by oriolfa on 2011-10-23
Favux, thanks for your quick reply. 

I'm not able to find wizardpen in oneiric repositories (I have the main, universe, restricted and multiverse checked in the sources). An Ubuntu Software Center or Synaptic search for xserver-xorg-input show lot of packages. Related to tablets I think there are the wacom (installed) and aiptek (not installed), also I have installed xserver-xorg-input-all, but I don't think it has the wizardpen driver inside.

It's a pitty that ubuntu only offers support for wacom and aiptek tablets, there are many low-cost tablets like mine (Trust) that should be supported. I really don't know how difficult is to add the wizardpen driver to the ubuntu branch, but it will solve many issues for all of non wacom tablets users.

By the way, does other people has the wizardpen driver available at the repos in oneiric?

Thanks!
Oriol.

---

### Post by oriolfa on 2011-10-23
ufff... SOLVED! 

Well, after all it was an stupid issue with the battery of the tablet pen. :oops:

the tablet is correctly detected by ubuntu oneiric and working fine, so I have to eat all my words about the support of ubuntu to these tablets. In these cases, in Spain we say "Tierra trágame..."

Sorry.
Thanks anyways for the help.
Oriol.

---

### Post by robalrr on 2011-10-30
Hi I have a Trust tb-6300. It is detected by ubuntu but I don't know how to calibrate it. I need to set the presure force and the dimensions, it is detected as usb-UC-LOGIC_Tablet_WP8060U-event-mouse. 

I have see that wizardpen is not available for ubuntu 11.10 anymore, the last version was for Natty.

In /usr/share/X11/xorg.conf.d I only have the following files:

10-evdev.conf 50-synaptics.conf  51-synaptics-quirks.conf
11-evdev-quirks.conf      50-vmmouse.conf
11-evdev-trackpoint.conf  50-wacom.conf

and I have installed xserver-xorg-input-all and added the ppa:doctormo/xorg-wizardpen

I think I need to know wich is the conf file I have to edit.

---

