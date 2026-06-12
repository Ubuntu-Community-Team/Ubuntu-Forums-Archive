---
title: "Toshiba Equium (satellite) A60 resumes to blank screen"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by Austin_KW on 2007-03-20
I have a Toshiba Equium (satellite) A60, it suspends and appears to resume but the display is blank so I can't really tell. This is not the toshiba bios, i think it is pheonix based by not sure.

the graphics is "ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05) and the driver is radeon.

Also what script is run on resume, I would like to reinitialise my wireless card, try an  rlogin to see what is the state of the sytem after a resume.

This is ubuntu 6.10

---

### Post by froghopper on 2007-03-20
Have you tried switching to a console (ctrl+alt+F1) and then back to X (ctrl+alt+F7) often this sorts out the blank screen. If you edit /etc/default/acpi-support you can force this switch every time with the DOUBLE_CONSOLE_SWITCH=true line. Otherwise add your wireless module to MODULES_WHITELIST="" and it will keep the network up over suspend. Scripts are in /etc/acpi/

---

### Post by Austin_KW on 2007-03-21
tried it, no joy, If only it were that simple. I took took a look at the scripts (thnx for the pointer)

If I remove the actual processor suspend and run the sleep/resume script then the display (and all the other devices) seems to be correctly handled; Everything restarts and my system seems ok. 

So then I tried to add some logging, but the sleep script never seems to return on wakeup. 
So either the processor context is not restored, or I have no disk/filesystem on wakeup.
Not sure how to go about debugging this, will have to give it some thought.

---

