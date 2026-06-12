---
title: "Proprietary nVidia driver and screen calibration"
date: 2011-04-10
forum: Hardware
---

### Post by Navyblue on 2011-04-10
I have a netbook that runs on Intel integrated graphic, Gnome's color management tool just works and I can calibrate my screen with Huey with no hassle.

I have a PC that runs on nVidia proprietary driver and the Gnome's color management tool apparently can't do that with the said driver. It looks like the nVidia software is overriding Gnome control.

Anyone managed to calibrate monitor with the proprietary nVidia driver?

---

### Post by realzippy on 2011-04-10
...nvidia-settings?

---

### Post by Navyblue on 2011-04-10
Nvidia settings does not allow the use of external calibrator like Huey.

---

### Post by cchhrriiss121212 on 2011-04-10
I think[ realzippy]("http://ubuntuforums.org/member.php?u=216523") meant that you should use the program "nvidia-settings" to calibrate your display, meaning you do not need any external calibration software. If you do not have it installed, check the software centre.

---

### Post by Navyblue on 2011-04-10
Thanks for your replies. :)

Yes with nvidia-setting there is options for gamma and things like that, but that is not good enough for me.

I need real calibration that measures actual screen output and generate hardware specific icc profiles (not some generic ones).

---

### Post by realzippy on 2011-04-10
Ok,understand.
Maybe this can help:

[http://www.nvnews.net/vbulletin/showthread.php?t=125017](http://www.nvnews.net/vbulletin/showthread.php?t=125017)


.................................................................
What happens when you delete the nvidia-settings.rc file which contains the color correction you do not want and then load your icc profile?
Think (don't know and can't test because I am not at my nvidia-machine in the moment)file gets recreated when rebooting.Nvidia driver should work without that file.
If this works somehow,a script could do that job...

---

