---
title: "Need Help Resuming"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by wwcameron on 2007-07-02
Hi,

I was able to get suspend to MOSTLY work in feisty using s2ram (uswsusp) as detailed in this link

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

The only thing that doesn't work is the USB. My mouse is dead when the machine resumes. However, if I plug in a usb memory stick or another usb mouse, the first mouse wakes up and everything returns to normal. So I figure I can put a script somewhere or configure something so my USB wakes up by itself. Anybody know what I should do exactly? I don't think the scripts in /etc/acpi/resume.d are being executed with uswsusp but I could be wrong.

Thanks

---

### Post by deruberhanyok on 2007-07-07
If it's a laptop this may not be useful, however if the machine is a desktop I hope this helps. I had a similar issue. I checked my motherboard's manual and found some jumpers for "USB device wake up". The setting explained that it was just for providing standby power to USB devices so they could be used (if set up) to wake up the machine from an S3 sleep mode.

I figured it might be worth changing the setting to see if it helped... so I changed it from the default "+5V" to "+5VSB" by moving the jumper and the devices now wake up properly.

---

### Post by wwcameron on 2007-07-10
Bingo!

You were right! I do have a desktop and switching the jumper solved the problem.

Thanks for posting.

---

