---
title: "Crash on Install - Laptop now a paperweight"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by wizardchef on 2009-09-18
I just tried to install xubuntu 9.04 on a Dell Latitude 700 MHz Pentium with 256 MB memory. I reset the boot disk in the bios (was running Windows 2000) and got the Xubuntu install screen, selected "Install." The CD loaded for about 45 seconds, then the install crashed with a "Shutting down ALSA" message. Now when I fire up the laptop I get about 1 second of error dump screen with the Shutting down ALSA message. No time to even read the messages.

I have no access to the bios, apparently, and no apparent access to the CD. Where do I go from here? 
:confused:

---

### Post by bruno9779 on 2009-09-18
there is no way you cannot access the BIOS because on and install CD. 
do you have a digital camera? that may help in understanding what are the dump scribbles you get for a second

---

### Post by wizardchef on 2009-09-18
Here is what I could get with a camera. Question marks mean I could not make out the message completely from the pic. The messages now scroll the top line off the screen.

-------------------
/etc/re%?/S89cron: 1: fail: Input/output error
*Starting periodic command scheduler crond
start/stop daemon: Unable to start/usr/sbin/cron: Input/output error?
Checking battery state ...
/dev/sda:
setting Advanced Power Management level to 0xfe (254)
*Setting up ALSA
.
.
.
(lots of these)

Shutting down ALSA

Laptop turns off. This all happens in about 2 seconds.

---

### Post by wizardchef on 2009-09-18
If I could get to the install CD again, I could try reinstalling Xubuntu again. But, I don't see a way to do that. How do you do that? If the bios is still intact, then why is it not trying to boot from the install CD instead of  trying to load the system??

---

