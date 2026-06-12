---
title: "Toshiba AC 100 and Ubuntu 12.04 LTS"
date: 2012-09-04
forum: Hardware
---

### Post by asgard2 on 2012-09-04
Hi,

I changed from Ubuntu 11.10 to 12.04 by using the instructions on [https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100).

On 11.10 I could change the backlight without root privileges.

With
> echo -n 40 > /sys/class/backlight/pwm-backlight/brightnessand a 99-backlight-permissions.rules file.
[http://ac100.grandou.net/backlightcontrol](http://ac100.grandou.net/backlightcontrol)

This is not working with 12.04. How can I fix that?

Under "Known issues" is nothing listet exept non graphic support. Does that mean flash, sound, encryption is also not working with 12.04?

Or should I change back to 11.10?

Thanks for helping :D

Regards, 
asgard2

---

### Post by asgard2 on 2012-09-06
as root it is possible to change backlight, it should be possible to make is usable for other users?

---

### Post by asgard2 on 2012-09-13
I changed read write backlight permissions for others:
"-rw-rw-rw- 1 root root 4096 Sep 13 12:12 brightness"

and it is working now.

Is a working flash player available?
The file player from the wiki is not working with 12.04 and the current firefox. [http://kotelett.no/ac100/phh/Android2.2/libflashplayer.so](http://kotelett.no/ac100/phh/Android2.2/libflashplayer.so)

---

