---
title: "Display on Inspiron 1100 blank during 1 of 3 boots"
date: 2009-05-01
forum: Hardware
---

### Post by mikegerard on 2009-05-01
Hi all-

I have an Inspiron 1100 running 9.04.

About every third boot the screen goes blank at the end of the boot process (I can hear the sound for the screen to enter your name and password).

I tried the Fn-F8 combination with no luck.  Usually I just power down and restart and then things display fine the next boot.

Any idea what could be causing this?

thanks,

Mike

---

### Post by Barry Carroll on 2009-05-01
When this happens you should be able to get to a console by doing a ```
ctrl + **alt** + f1
``` and then have a look at the log to see what has gone wrong ```
cat /var/log/Xorg.0.log
``` looking out for lines starting with (EE) to see any errors.

When you are there you can try to start up the graphical login again by doing a ```
sudo /etc/init.d/gdm restart
``` to see if that will bring it up.  If that fails you can shutdown ```
sudo shutdown -h now
``` or reboot ```
sudo shutdown -r now
``` safely.

---

### Post by SnackMasterX on 2009-05-07
I am having the same issue with my friends Inspiron 1100, has anyone had any luck in resolving this issue?

---

### Post by sboutwell on 2009-09-07
Bump... Same issue here.. So far it's not liked the INTEL driver fix of just going to VESA drivers..  Anyone found a fix for this.

---

### Post by perlwonk on 2009-10-28
I'm having the same problem. I can hear it finishing up the boot up but there's no video on the laptop monitor. I put in my user name and password, and it logs me in. Then if I press Ctl-Alt-F1, I get the command prompt. 

I searched the log file suggested on an earlier post, but there is no line that starts with (EE). I have no clue how to fix this. For me, the display was normal after I first installed 9.04, but then after a couple of reboots, the video just stopped working. Now, I can see video while the BIOS is doing it's thing, then I see "Ubuntu", then it goes blank. Any help would be great. Thanks.

---

### Post by mgoodfellow on 2009-10-28
Having similar issues on an Inspiron i8200.  It worked fine until I used the Hardware Drivers app to add the nVidia driver, then the screen powers off immediately after the boot.  I have tried disabling the power management options in the BIOS as suggested on another forum, didn't work.  Any help would be appreciated, will post here if I find a solution.

**Update**
**Solution**
Ubuntu is recognizing a phantom monitor attached to the external port.  Can be solved by editing xorg.conf:

From the command prompt:
[I][B]sudo nano /etc/X11/xorg.conf

[/B][/I]Scroll down to Section "Device"
add:
***Option "****UseDisplayDevice" "DFP-0"***

reboot:
[I][B]sudo reboot

[/B][/I]Hope this helps

---

