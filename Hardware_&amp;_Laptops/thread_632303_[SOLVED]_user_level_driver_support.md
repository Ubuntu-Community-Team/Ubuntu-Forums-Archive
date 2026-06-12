---
title: "[SOLVED] user level driver support"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by hvac3901 on 2007-12-05
This is what was said to be the issue....
"You should see the "Password or swipe finger:" prompt when trying to sudo or su. If you don't, you probably do not have the "**User level driver support**" compiled into your kernel or the "**uinput**" module loaded!"

I have loaded thinkfinger 0.3 on my thinkpad and it works fine from the terminal, saves fingerprints and tests out just fine, but in actual use it doesn't function to request a fingerprint. . STILL So MUCH TO LEARN.

---

### Post by hvac3901 on 2007-12-05
An update.

using the command in terminal sudo modprobe uinput

I am able to utilize my fingerprint reader to substitute password entry on all su functions i.e. package manger and in the trminal. Now that is only good for one session and needs to be restarted every time the system is rebooted. How can i make UINPUT load on start-up??

---

### Post by hvac3901 on 2007-12-05
NEVERMIND,,,i found it...

[http://ubuntuforums.org/showthread.php?t=584335&highlight=uinput](http://ubuntuforums.org/showthread.php?t=584335&highlight=uinput)

---

