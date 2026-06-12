---
title: "ACPI S3 Sleep on the Radeon gfx adapter"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by fa2k on 2005-04-03
I am using the radeon driver with a Mobility Radeon card. Resume from S3 works sometimes, but it is very unstable. Which driver is recommended for ACPI power saving with radeon cards, and what settings do I need to apply?

edit: the driver is for X. I don't know if I use another driver for the system. The error: screen is filled with vertical lines of different widths and colors in graphics mode, and is black and may have white spots in console mode.

---

### Post by fa2k on 2005-04-06
I have also tried the ati driver, but the "fglrx" doesn't seem to support my 7500-card. I am willing to debug the radeon driver. I have no previous experience with hardware interfacing, so I will need some help. Is  there any howtos on driver programming or preferably debugging in Linux?

---

### Post by fa2k on 2005-04-08
Just in case anyone is interested, it seems to work now. It might have been a bug in the [FONT=Courier New]resume.sh[/FONT] script, but I'm not a great shell scripter, so I'm not sure what was the cause (I added quotes somewhere and rearranged the actions). Now I am using the Save VBE state and POST Video card options in the /etc/default/acpi-support, and a slightly modified version of the resume.sh script. I added a pause (sleep 1) after POSTing the video card, but I don't dare to even touch(1) the file because it has worked 3/3 times and I am happy about that. :grin:


Edit: Then it didn't do 4/4, then I removed the save VBE and POST, now it's done 3/3 again, but I have a few more tricks to try if it fails the next time;)

Edit2: I'm out of ideas. And I doubt developers will bother with fixing a so old card. Maybe I'll go back to windows...:(

---

