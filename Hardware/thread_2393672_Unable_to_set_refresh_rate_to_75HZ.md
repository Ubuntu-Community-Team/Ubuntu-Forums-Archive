---
title: "Unable to set refresh rate to 75HZ"
date: 2018-06-06
forum: Hardware
---

### Post by tannisroot on 2018-06-06
Hello. I am using Ubuntu 18.04 with proprietary nvidia drivers (390.59) installed. I have a monitor that supports progressive refresh rate up to 75HZ in 1080p, and it does work in such mode in Windows, I set it manually in nvidia control panel. However, I am unable to do so in Nvidia X Server Settings, as it just doesn't let me choose refresh rate higher than 60HZ. I looked up online that I can do so by running xrandr command, so i ran "xrandr --output HDMI-0 --mode 1920x1080 --rate 75". However, when I did that, the image on my monitor just became shaky and unusable. There was also this guide about adding custom EDID file option to xorg.conf but that just result in my system not being able to start in graphics mode.
I really like playing games in wine on my system and it would be nice to play them with a picture that's a bit more smooth. Is there any way I can do this?

---

### Post by pqwoerituytrueiwoq on 2018-06-08
HDMI does not support more than 60hrz at 1920x1080
using that command seems to work here, but the lose is color quality is unacceptable
xubunut 18.04; nvidia 390.48; gtx 650 ti boost

---

### Post by Yellow Pasque on 2018-06-10
> **pqwoerituytrueiwoq said:**
> HDMI does not support more than 60Hz at 1920x1080

That's early HDMI (before version 1.3).

---

