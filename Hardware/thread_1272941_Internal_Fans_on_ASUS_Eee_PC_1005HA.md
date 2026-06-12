---
title: "Internal Fans on ASUS Eee PC 1005HA"
date: 2009-09-22
forum: Hardware
---

### Post by butterbridge on 2009-09-22
I'm using Ubuntu 9.04 (NOT Netbook Remix, it wouldn't work correctly even after 2 separate installs) on my ASUS Eee PC 1005 HA-V and I was wondering if anyone knew if it were possible to turn the internal fan speed up.  I tried using the Eee PC system tray applet, but much to my extreme annoyance it kept switching to super performance mode every time i plugged in the AC or woke it from standby (even on battery power), this caused it to get HOT and would knock the keyboard offline.  I uninstalled the Eee PC utilities and have noticed it remains much cooler on AC power than it did under super performance mode.

My issue is I would like to have some kind of manual control over the internal fans since I am still paranoid about internal heat after my last laptop's battery ruptured from excessive heat.  I am not annoyed with fan noise as other people seem to be, I personally don't care if its running perfectly silent or is making a tiny bit of noise.  Windows seems to adjust fan speed very well automatically, but linux does not.  If it is part of the Eee PC utilities that manages fan speed, is there then a way to permanently prevent it from automatically changing out of low performance mode? 

Sorry for the long post, but if anyone could point me in a good direction.  By the way I am for the most part a complete n00blet at linux, so if you have a solution try to break it down very simply for me.

Thanks,
Butterbridge

---

### Post by frecon on 2009-10-02
Try setting this in the eee-pc systray applet. (right click and choose edit configuration)

```
# Fix fan bug
FAN_MODE=”auto”
```

---

### Post by imaqt55 on 2009-12-15
> **frecon said:**
> Try setting this in the eee-pc systray applet. (right click and choose edit configuration)

```
# Fix fan bug
FAN_MODE=”auto”
```

Could you tell me what you mean by this? I am having the same problem with my fan control now that I have upgraded to 9.10 NBR. The Eee icon in the tray allows me to left click and turn on/off wireless, camera, and card reader. It has an option for Performance, where I used to be able to select powersave in 9.04, but now there are no options in that menu.

If I right click, my options are Preferences (which control the hotkeys), About, and Sensors. I'd like to know how to edit the configuration, as you said.  I am also new to Linux. Any help is appreciated.

---

### Post by frecon on 2009-12-17
> **imaqt55 said:**
> Could you tell me what you mean by this? I am having the same problem with my fan control now that I have upgraded to 9.10 NBR. The Eee icon in the tray allows me to left click and turn on/off wireless, camera, and card reader. It has an option for Performance, where I used to be able to select powersave in 9.04, but now there are no options in that menu.

If I right click, my options are Preferences (which control the hotkeys), About, and Sensors. I'd like to know how to edit the configuration, as you said.  I am also new to Linux. Any help is appreciated.

If I remember right the developer of the eee app you are using stopped the development and didn't do a version for 9.10. There's more info on his blog somewhere. It was something about that with every Ubuntu release a lot of stuff breaks and he have to fix them.

---

### Post by imaqt55 on 2009-12-17
Well that would explain that.  Still, shouldn't the fan come on when the computer gets hot?  Any idea how to make this happen?  It only comes on if it is hot and I restart the computer.  The other day it got so hot and the fan never came on, and suddenly the computer just turned off.

---

### Post by frecon on 2009-12-17
> **imaqt55 said:**
> Well that would explain that.  Still, shouldn't the fan come on when the computer gets hot?  Any idea how to make this happen?  It only comes on if it is hot and I restart the computer.  The other day it got so hot and the fan never came on, and suddenly the computer just turned off.

I would uninstall all the eeepc program. I have no trouble with heat with mine in ubuntu 9.10. The fan comes on if it's starting to get hot. I even have some troubles with the fan spinning at max when the computer is not hot...

Good luck.

---

