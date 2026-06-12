---
title: "Printer Problem!"
date: 2005-11-11
forum: General Help
---

### Post by SunshineSmile on 2005-11-11
I am desperately trying to have a z601 lexmark print my documents. There is an install guide on the forum:  [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

Well, I try to set my printer up according to it, but I get the following error message in the LAST STEP!!

myname@hostname:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

What does this error message mean?

The driver of my printer is recognized, and although it says that it is preparing a print out when I click on the print icon on e.g this page, no page actually comes out of that "!#¤% printer.

I noticed something suspicious in my device manager:
Key: usb_device.can_wake_up Type: bool Value: False

Anybody have a clue what is missing/how to get that lexmark working?

---

### Post by kleeman on 2005-11-11
Try this:

sudo apt-get install libstdc++5

and then retry your last step.

---

### Post by SunshineSmile on 2005-11-12
and now it works!!! (at least I got a page with bad print) Thanks a lot!!

---

