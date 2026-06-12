---
title: "USB to OBD-2 Cable"
date: 2008-10-14
forum: Hardware
---

### Post by natewiebe13 on 2008-10-14
I have a USB to OBD-2 Cable that I use for automotive diagnostics with AutoEnginuity ([http://www.autoenginuity.com/](http://www.autoenginuity.com/)). AutoEnginuity is for Windows and I used wine to install it (installed and runs perfectly). The problem I am having, is that the cable shows up in /dev/usb as hiddev0, when I create a symbolic link in .wine/dosdevices as com1, the program says, "unable to open com port 1". When I unplug and plug in the cable the other devices that show up in /dev are hidraw0 and a bunch of other ones labeled usbdevice3.1ep00 (not sure on the exact name for the last one mentioned) ive tried it with both hiddev0 and hidraw0 and neither work. i also heard that a problem may be the baud rate, but i dont know how to check the rate (supposed to be 19200 for autoenginuity) Any ideas anyone?
thanks in advance

---

### Post by andersja on 2009-08-06
Did you have any luck in getting this working? If yes, it'd be great if you could share! :-)

---

### Post by natewiebe13 on 2009-08-06
havent gotten this to work yet. i was using wine to get autoenginuity to work and wine hasnt been able to get hardware over yet.

---

### Post by wyrless2002 on 2009-11-22
Does this thread help? I'm just reading right now, I've not implemented any of this, but it seems that they were on a similar hunt in the other thread and may have found a solution. Good Luck, Let us know if this did the trick.

[http://ubuntuforums.org/showthread.php?t=1264807](http://ubuntuforums.org/showthread.php?t=1264807)


Here's one more tutorial that I've found that details the process:
[https://www.scantool.net/forum/index.php?action=printpage;topic=3086.0](https://www.scantool.net/forum/index.php?action=printpage;topic=3086.0)

---

### Post by lkraemer on 2009-11-27
Have a look at how I got mine working.
[http://ubuntuforums.org/showthread.php?t=1339775](http://ubuntuforums.org/showthread.php?t=1339775)

lk

---

