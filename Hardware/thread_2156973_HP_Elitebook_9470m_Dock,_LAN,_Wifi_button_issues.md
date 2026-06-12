---
title: "HP Elitebook 9470m Dock, LAN, Wifi button issues"
date: 2013-06-23
forum: Hardware
---

### Post by windfix on 2013-06-23
I am mostly posting this to help others with the this hardware, or those considering it. I got the HP Elitebook 9470m and it's ultraslim dock, running Ubuntu 13.04 alongside Windows 7. It's an awesome machine. My favorite part is using dual monitors with the dock, and having it flawlessly undock and redock without any reconfiguration or hacking.  It makes grabbing the machine for meetings and returning to the office a cinch.  With the SSD, this thing is fully booted in 21 seconds.

That said, there are a few issues:
[LIST]
[*]The LAN port (rj45) on the laptop itself does not work under Ubuntu.  The DOCK's port works fine.  Annoyance, but not huge - I'm on wifi when not docked.
[*]The wifi on/off switch does not work under Ubuntu.  Again, not huge deal, but annoyance.
[*]The fingerprint reader is unrecognized in Ubuntu.  Not a huge issue, but it would be nice if that worked. I have fingerprint GUI 1.05 installed, but no device recognized.
[*]Weirdest... the displayport on the dock worked fine for a month, then just stopped working.  HP replaced it with overnight delivery, their service as incredible.  However, it happed 3 days later on my dock at home.  HP replaced again.  When it happened days later on the replacement dock at home, I had to conclude it was not the dock.  Ironically, booting into Windows - it worked again; AND it started working under Ubuntu again.  An odd reason to have to boot Windows, but this observation may save someone else a headache.
[/LIST]

If anyone knows how to get my fingerprint reader going, give me a shout.  The device (from lsusb) is:
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc.

---

### Post by Toz on 2013-06-23
> **windfix said:**
> I am mostly posting this to help others with the this hardware, or those considering it. I got the HP Elitebook 9470m and it's ultraslim dock, running Ubuntu 13.04 alongside Windows 7. It's an awesome machine. My favorite part is using dual monitors with the dock, and having it flawlessly undock and redock without any reconfiguration or hacking.  It makes grabbing the machine for meetings and returning to the office a cinch.  With the SSD, this thing is fully booted in 21 seconds.
I have the same notebook. Love it as well.

> That said, there are a few issues:

> The LAN port (rj45) on the laptop itself does not work under Ubuntu.  The DOCK's port works fine.  Annoyance, but not huge - I'm on wifi when not docked.
Have never tried the onboard ethernet port - will try when I have some time.


> The wifi on/off switch does not work under Ubuntu.  Again, not huge deal, but annoyance.
I fixed this with some kernel parameters. Specifically, **acpi_osi= acpi_backlight=vendor**. This also fixed the brightness function keys.


> The fingerprint reader is unrecognized in Ubuntu.  Not a huge issue, but it would be nice if that worked. I have fingerprint GUI 1.05 installed, but no device recognized.
Fingerprint reader? Hmmm. This one doesn't seem to have one.


> Weirdest... the displayport on the dock worked fine for a month, then just stopped working.  HP replaced it with overnight delivery, their service as incredible.  However, it happed 3 days later on my dock at home.  HP replaced again.  When it happened days later on the replacement dock at home, I had to conclude it was not the dock.  Ironically, booting into Windows - it worked again; AND it started working under Ubuntu again.  An odd reason to have to boot Windows, but this observation may save someone else a headache.

Haven't had any issues with the dock at all. Mind you, I only use Xubuntu on it.


I have found one further issue that I haven't been able to solve yet. When plugging in headphones, the sound is very tinny - like the bass is missing (oddly enough, works fine through the dock). Turns out the sound card isn't officially supported by the version of alsa that is installed with 13.04. Am waiting for official support.

---

### Post by grahamhayes on 2013-09-24
The only issue I currently have is the fingerprint scanner, it seems that there is drivers for the RHEL / Fedora / SUSE linux side, but they don't seem to work on 13.04.

My onboard wired ethernet port works great.

To get the screen brightness to work, I added **acpi_osi=\"!Windows 2012\"" **kernal parameters, seems to have got all the buttons to work.

---

### Post by Toz on 2013-09-24
> **grahamhayes said:**
> To get the screen brightness to work, I added **acpi_osi=\"!Windows 2012\"" **kernal parameters, seems to have got all the buttons to work.
Yes, that got my brightness to work as well, but it didn't fix the wireless on/off button. **acpi_osi= acpi_backlight=vendor** gets both the brightness and wireless switch to work.

Out of curiosity, do you get tinny (poor quality) sound when you plug in earphones into the combo jack as well?

BTW, welcome to the forums.

---

### Post by riccardosl45 on 2014-01-04
did you manage to find drivers for fingerprinter scanner? is it possible to use it in ubuntu for login?

---

