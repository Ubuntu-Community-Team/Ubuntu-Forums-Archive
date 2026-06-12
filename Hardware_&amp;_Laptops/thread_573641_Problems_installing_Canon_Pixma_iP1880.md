---
title: "Problems installing Canon Pixma iP1880"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by Mogmi on 2007-10-11
I don't seem to be able to install my new Canon Pixma iP1880 on my thinkpad r40 running Feisty. I've tried a few things, namely using the drivers in the .deb packages discussed in: [http://ubuntuforums.org/showthread.php?t=445874](http://ubuntuforums.org/showthread.php?t=445874) that are supposed to be Ubuntu-friendly.

Also tried following the instructions at [http://ibr94.blogspot.com/2007/08/canon-pixma-ip1880-printer-in-ubuntu.html](http://ibr94.blogspot.com/2007/08/canon-pixma-ip1880-printer-in-ubuntu.html) using alien to transform Canons .rpm files to .deb (also fixed libtiff.so.3 and libpng3 as described there).

What happens is (same result with both methods above) that everything seems to be fine during the installation, that is the printer is autodetected and I can add it using the iP1800-drivers. But when I try to print a test page the only thing that happens is that the printer starts blinking with an orange light - it keeps doing that until I manually restart it and that's it. 

Cups gives the error message: "Ready: Unable to write print data: No such device" 
I've also seen other error messages, but can't reproduce them now. 

Any help at all would be very appreciated - this is driving me mad - especially since no one else seems to have these problems.

---

### Post by Mogmi on 2007-10-16
Ok, I finally sorted this out. When I installed the printer on a MacBook I got an error message from the printer saying that it couldn't determine how much ink was left in the cartridge - but that if I wanted to print anyway I should press the orange blinking button and hold it for 6 seconds. After I did that once it works just fine with both OSX and Linux. 

As always the problem lies in the drivers for Linux not being  as good as those for Win or OSX :-|

So if anyone is experiencing the same thing, press and hold the orange button for a long time and that will probably fix it.

---

