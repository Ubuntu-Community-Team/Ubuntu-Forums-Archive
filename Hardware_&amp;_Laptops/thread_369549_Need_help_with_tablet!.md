---
title: "Need help with tablet!"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by Mazin on 2007-02-24
I need help with a tablet I have.

It doesn't show up in any programs as an extended input device (gimp, inkscape, etc.).

Using evtest,  I can see the absolute coordinates and pressure data.  This means that it can get all the info, but apparently usbhid can't present it properly to userspace or something.

Since I can already "see" the information, how do I make it an extended input device?

---

### Post by bwiewiora on 2007-03-03
I'm guessing you're talking about getting the touchscreen working--what model is your tablet?  If it is a Fujitsu Stylistic 3400/3500, this thread might be useful:

[http://ubuntuforums.org/showthread.php?t=159373]("http://ubuntuforums.org/showthread.php?t=159373")

Here's a thread for a Toshiba M205:
[URL="http://http://www.ubuntuforums.org/showthread.php?t=371510&highlight=tablet"]
http://www.ubuntuforums.org/showthread.php?t=371510&highlight=tablet[/URL]

If you have a different model, try searching specifically for that one in the forums.

---

### Post by Mazin on 2007-03-03
I've gotten it somewhat functional using the evdev driver for X.  It still has problems, though.  Pressure sensitivity doesn't work, even though it shows up in evtest.  Absolute coordinates work.  Y movement works perfectly, but X movement is very jerky.

Does anybody know how to use evdev?

---

### Post by themischiev on 2008-06-26
Stylistic 3400 Harddrive Image For Download?

Please Someone Have An Image Of The Fujitsu Stylistic 3400 Hard Drive With Ubuntu Installed That I Could Download And Copy To My Stylistic 3400 Hard Drive?

---

### Post by Mazin on 2008-06-26
Hey, quit spamming the forum over and over with the same bad question.  You just dug up a thread that was over a year old.  Nobody's going to help you like this.

---

