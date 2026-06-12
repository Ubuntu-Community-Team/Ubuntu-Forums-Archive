---
title: "Strange problem with xserver-xorg after upgrade to Jaunty"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by supradave on 2009-04-29
Just upgraded machine and on reboot get the error that it is running in low-graphics mode (which it isn't, running 1280x1024), and then attempt to reconfigure and that doesn't work.  If I continue running in low-graphics mode (which it isn't, running 1280x1024), it starts up a second X session running at 1280x1024.  Everything seems normal, except it won't startup normally.  The failsafe log indicates success while the Xorg.0.log indicates failure.  Stopping gdm and removing from with update-rc.d and rebooting and trying startx fails.  Rebooting and doing /etc/init.d/gdm start starts up as above.  /etc/init.d/gdm restart doesn't do anything different.  I have removed all xorg.conf files (moved them, at least).  I have removed xserver-xorg and installed xserver-xorg to no avail.  I just don't get it.

lspci:
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

/etc/X11/xorg.conf
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Thanks for the help.

---

### Post by LarsO on 2009-06-05
Same problem for me, started with 8.10 - 9.04 and 9.10 do the same. 8.04 runs fine. If I drop to command line, I can start a desktop with "startx" and everything runs fine. The xorg.0.log is exactly the same as the 8.04 I run normally.

Edit: I was able to fix it using the information on [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)
After going through the xorg log with a fine tooth comb I realized there was no response from the monitor on the DDC probe. and it messed things up.
I used my xorg.conf file from my 8.04 install and tweaked it a bit to clean it up and added the following lines to the device section:
  Option "NoDDC" "true"
  Option "IgnoreEDID" "true"

You have to make sure the xorg is configured quite completely as it's basically not trying to configure automatically anymore. I hope it works for you too.

---

