---
title: "&quot;Out of timing&quot; error on GRUB boot menu and ttys"
date: 2012-10-05
forum: Hardware
---

### Post by Barhilton on 2012-10-05
When I turn on my computer, the monitor goes blank and the message "OUT OF TIMING V:58Hz H:92kHz" (although its possible that the numbers change, I haven't checked). The grub menu does not appear (meaning that I cannot boot into windows, which is the main reason this is annoying me), nor does the loading bar. After a short wait, the login screen of 12.04 appears. The same error appears when I press alt+F1-6 to enter a tty. Please help!!

---

### Post by oldfred on 2012-10-05
Does recovery mode boot to a terminal?

Not sure if this may help:
Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub

---

### Post by Barhilton on 2012-10-20
Running "rm ~/.config/monitors.xml" fixed the problems with the ttys. Changing the resolution with Grub Customizer fixed the problem with grub. Thanks!

---

