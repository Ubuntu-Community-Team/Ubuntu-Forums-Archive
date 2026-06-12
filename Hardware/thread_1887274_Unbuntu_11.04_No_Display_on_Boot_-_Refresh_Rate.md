---
title: "Unbuntu 11.04 No Display on Boot - Refresh Rate?"
date: 2011-11-26
forum: Hardware
---

### Post by Tim13 on 2011-11-26
Hello,
I'm having a monitor refresh rate issue while booting 11.04 (display goes blank). I believe this to be a refresh rate issue as the documented CRTL+ALT+NumPad+ did enable me to see the log in screen. I've installed Start-Up Manager and made the documented changes, but this did not work. I've read various solutions regarding Xorg, but I do not have a good enough understanding of the /usr/share/X11/xorg.conf.d/ configuration. BTW, my video card is an ATI 8500LE (R200). ATI drivers have known issues, but seem to work properly once logged in?

Is the monitor refresh rate my problem? If so, can I set the monitor refresh rate on boot after the GRUB menu? My monitor is correctly recognized once logged in. Thank you.

---

### Post by gordintoronto on 2011-11-26
It's perfectly normal to have a blank screen during part of the boot process. Are you saying the login screen does not appear?

This has nothing to do with solving your problem, but I'm a little surprised you are using 11.04, since it is not current, and it's not a long-term release. In my opinion, 11.10 is a significant advance over 11.04.

---

### Post by Tim13 on 2011-11-27
Thanks for the reply Gord. Yes, the login screen does not appear. If I use CRTL+ALT+NumPad+ and hit NumPad+ about 15-20 times, the login screen does appear.

I would like to upgrade to 11.10, but I'd prefer to solve this issue first. Unless the refresh rate issue is fixed in 11.10? I've used Debian and many previous releases of Ubuntu and never had this difficulty.

---

### Post by gordintoronto on 2011-11-27
You have not mentioned the brand and model of your monitor. 

I'm not sure why you think this is related to the refresh rate, perhaps because I don't recognize the Ctrl-Alt-Numpad key combination. My keyboard has no key called "numpad."

11.10 uses a different program at startup, something called "lightDM." I don't understand the technical details.

I have never done an "upgrade," since many of the messages in the forums complain about problems caused by this approach. I backup, backup, backup, and install from scratch. I have separate / and /home partitions, and I have never actually lost any data, but there are points when a couple of bad mouse clicks would blow away everything.

---

