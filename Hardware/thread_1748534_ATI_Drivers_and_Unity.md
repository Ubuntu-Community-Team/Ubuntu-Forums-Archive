---
title: "ATI Drivers and Unity"
date: 2011-05-03
forum: Hardware
---

### Post by nosushi4you on 2011-05-03
Hello everyone,
It's literally been years since I've been to this forum. I took a long break from linux, but the arrival of Ubuntu 11.04 piqued my interest yet again. So, here is what's not working:

I have an HP laptop with switchable graphics. They are an Intel HD card and an ATI Radeon HD 5650. After I install and boot Ubuntu, Unity loads fine. This is before I installed the Additional Drivers for my ATI card. If I install the drivers, a popup appears that says my hardware does not support Unity, and GNOME loads instead. I really like Unity, and would love to continue using it. So, I figured, I'll just uninstall the drivers. Unity works again after doing this, but I am now faced with a much bigger problem: Ubuntu will not load nine out of ten times. If I do not had the Propriety driver for my graphics card installed, then more often than not, when I select Ubuntu from GRUB, my screen goes black and the system will boot further. If I reinstall the drivers, the system boots correctly, but I don't have Unity. So, I am kind of between a rock and a hard place here: If I have the propriety drivers installed, I can boot but do not have Unity, and if I uninstall the drivers, Unity works, but it takes many tries to get Ubuntu to load successfully. 


Any suggestions? Thanks. :)

---

### Post by nosushi4you on 2011-05-03
Really, I would be fine using the drivers Ubuntu ships with, as opposed to the proprietary drivers (fglrx). They work fine if I can get the system to load. Any idea how I might be able to get Ubuntu to load? As stated before, it works brilliantly once it loads, and it does indeed load sometimes, just not all times.

---

### Post by erikschmitz on 2011-05-03
I'm having similar issues with my dv6t -- it has switchable graphics between Sandy Bridge HD3000 and a Radeon 6770. 

Booting into the system is flaky with the default drivers. 

The ATI drivers in the repos and the 11.4 drivers on the ATI website both disable Unity, and don't detect the ATI card at all once they're enabled.

Supposedly the 11.4 drivers have support for switchable graphics but I'm guessing they don't have any support at all for the 6XXX series yet...

---

### Post by nosushi4you on 2011-05-04
What is most interesting to me is what causes the system to boot correctly only some of the time. Something is obviously working correctly when it boots up.

---

### Post by tossman101 on 2011-05-04
I am having a very similar problem with a Radeon 5670.  I've been trying to find a fix, but I've seem to hit a wall, anyone with a lead would be a great help.  (I'm still learning this stuff)

---

### Post by sauthess on 2011-05-04
Hi,

Do you have a kernel panic at start like in this bug : 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620")

If yes, it's a bug between radeon module and i915.

A "solution" I have found to boot without any problem is to blacklist radeon :
echo "blacklist radeon" > /etc/modprobe.d/blacklist-radeon.conf
update-initramfs -u

other solution is to add "radeon.modeset=0" at boot time

It "works" when you installed fglrx driver because this driver blacklist radeon module (to be able to handle the graphic card itself...)

I have i5 + HD 5470 so I think you are in the same situation.

if your in this case, indicates that your impacted too to this bug...

---

### Post by herzal on 2011-05-18
> **erikschmitz said:**
> I'm having similar issues with my dv6t -- it has switchable graphics between Sandy Bridge HD3000 and a Radeon 6770. 

Booting into the system is flaky with the default drivers. 

The ATI drivers in the repos and the 11.4 drivers on the ATI website both disable Unity, and don't detect the ATI card at all once they're enabled.

Supposedly the 11.4 drivers have support for switchable graphics but I'm guessing they don't have any support at all for the 6XXX series yet...

same here, I contacted the AMD support. They replied that HP changed some hardware ID's and therefore the official driver does not recognize the card, and that I should use the linux driver provided by HP (which does not exist).

---

### Post by fcomstoc on 2011-08-13
> **erikschmitz said:**
> I'm having similar issues with my dv6t -- it has switchable graphics between Sandy Bridge HD3000 and a Radeon 6770. 

Booting into the system is flaky with the default drivers. 

The ATI drivers in the repos and the 11.4 drivers on the ATI website both disable Unity, and don't detect the ATI card at all once they're enabled.

Supposedly the 11.4 drivers have support for switchable graphics but I'm guessing they don't have any support at all for the 6XXX series yet...


I had an issue with this card as well, I have an ATI HD 6770, I installed Fedora 15 (I know its not Ubuntu) and after i restarted I got a message stating that Gnome 3 (the fedora default is not supported) after I changed to dual screen mode and restarted again the GUI wouldn't load at all.

I don't know what the deal is with these graphics cards but I own 3 and have never had a good experience getting them to work on any distro

---

