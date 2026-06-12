---
title: "b130 video broken after jaunty upgrade (with solution)"
date: 2009-05-09
forum: Hardware
---

### Post by cybertoast on 2009-05-09
Had a problem after I upgraded my Dell Inspiron B130 from Intrepid to Jaunty. The video completely got screwed up to the point where the machine was basically unusable. Tried a number of different things, and finally solved the problem. Decided to post my steps in case others have a similar issue.

**Problem**
* After upgrade the system starts up and progress bar is fine (the initial Ubuntu icon startup progress bar).
* Screen flashes a few times with vertical colored bars on either side of the screen, black in the middle
* Startup proceeds to the login screen, but the video is distorted to the point of being unusable. I can vaguely see that there's a background and a login dialog somewhere on the screen, but I can't navigate in any way (mouse or keyboard) and I only know that the dialog exists because I expect to see it!

After this point the system is completely unusable. Ctrl-alt-backspace, ctrl-alt-delete or any other key combination is futile. The only solution to restart is to do a hard reboot by holding down the power button for 10 seconds.Solutions that didn't work:
dpkg-reconfigure xserver-xorg
dpkg-reconfigure -phigh xserver-xorg
uninstall and reinstall xserver-xorg intel, ati, nvidia drivers (apt-get uninstall xserver-xorg-video-intel)

**Final solution**
The only solution that worked is to remove and reinstall xserver-xorg. Fortunately the process is simple:
1. Boot into recovery mode (latest kernel version would probably be best)
2. Drop to network root shell
3. apt-get remove xserver-xorg
4. apt-get install xserver-xorg

The system now works like a charm!

---

### Post by studavis on 2009-06-30
Hi, I've got similar problem with Intel. I tried your final solution butI get message to say it cannot find the files. from which directory do you execute those 2 commands? thanks

---

