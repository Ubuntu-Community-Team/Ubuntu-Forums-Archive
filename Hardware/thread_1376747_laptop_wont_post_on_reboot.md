---
title: "laptop wont post on reboot"
date: 2010-01-09
forum: Hardware
---

### Post by bruhja on 2010-01-09
Hey all I have a Toshiba satellite P20 with a fresh install of Karmic. my laptop will boot into Karmic ant everything goes just fine until i try to restart. Ubuntu will shut down properly cleanly and **_FAST_** , however when my laptop tries to power up it wont post just sits on a blank screen with the fans running (I can also hear the dvd ROM do its boot up) but nothing else. 

This also happens when i select shutdown, everything happens exactly as stated above except that the laptop will power down completely, however the laptop will not post when i power it back up. I have to completely remove the power Mains and the battery then the laptop will post correctly.

Hibernate will also leave me on a blank screen with out any responsiveness when attempting to wake it up.

On a side note i managed to get the suspend to work by editing "ect/default/acpi-support" file and altering the line "ACPI_SLEEP_MODE=" from default setting(=true i think) to "ACPI_SLEEP_MODE=standby". thus switching from ACPI S3 sleep mode to ACPI S1 sleep.

All help would be greatly appreciated as i have been fighting with this for a week and all searches have become exhausted.

---

### Post by bruhja on 2010-01-10
anyone any ideas????

---

### Post by sideburns on 2010-01-10
POST (Power On System Test) finishes before Grub starts and long before Ubuntu.  If you're having trouble with it, it's hardware, not software.

---

### Post by bruhja on 2010-01-11
Funny thing is i never had this problem with winblowz only with Ubuntu.

Even funnier is that the morning after i posted this thread the laptop started to post properly after shut down. 

Next i guess I'll try restart then hibernate and see if they work now too.

---

### Post by bruhja on 2010-01-11
Nope the restart command still will not post(forcing me to remove all power supply), and the hibernate/suspend feature just seems to initiate my screen-saver. I'm confused.

---

### Post by PapaRaven on 2010-01-21
Same issue with Toshiba Satellite P35-6292.  Just so no-one spins their wheels in the Xorg arena: also happens with Karmic Minimal System (from the server CD), i.e. w/o Xorg.

I won't argue whether or not it is Toshiba's damage.  But that OS, which is dominant in our industry, absolutely *can* reboot every time without issue.
(conspiracy?)

:confused:

---

