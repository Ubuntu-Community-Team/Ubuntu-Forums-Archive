---
title: "Random Freezes on 12.04 64-bit"
date: 2013-05-01
forum: Hardware
---

### Post by kendoori on 2013-05-01
Thinkpad x230 + Ultrabase and External monitor, 12.04 w/Gnome shell. I will admit to living dangerously and took the SSD out of my former X201 and moved it into the X230. All is seemingly working properly, except for random freezes. Machine literally freezes 2-3x a day. Can't kill it from SSH on another machine, and Ctrl+Alt+F1 does nothing, and Alt+PrtScrn+REIUSB also does nothing. Popping the battery is only remedy.

The machine doesn't feel especially hot. Am running the Shell extension for temperature and it fluctuates between 48 - 55 degrees C.

I do run Virtualbox often, and thought for a while this had to do with some virtual machines. Also thought it might be Chrome, and just switched to Chromium prior to last crash.

I'm green about deciphering the Ubuntu logs, but would like to somehow pinpoint why it's freezing before I go ahead and wipe and reinstall (not looking forward to doing this, but realize that this maybe the only clean path to known good system).

Any advice is appreciated.

---

### Post by ebyeby6 on 2013-08-06
Did you stick to the default kernel for 12.04? Type "uname -r" in a terminal at it will tell you the current kernel. If you are running 3.2 that could be the issue.

---

### Post by kschiff on 2013-08-06
Upgrade to 13.04 solved this problem :-)

---

