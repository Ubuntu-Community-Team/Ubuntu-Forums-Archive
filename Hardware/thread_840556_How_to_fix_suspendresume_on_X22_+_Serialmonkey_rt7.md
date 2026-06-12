---
title: "How to fix suspend/resume on X22 + Serialmonkey rt73"
date: 2008-06-25
forum: Hardware
---

### Post by David_G_D on 2008-06-25
Hi, Since I've been using the Serialmonkey rt73 driver for my USB wifi adapter, (Edimax EW-7318USg) APM suspend and resume don't work.  Here's how I made it work:

I made the file /etc/apm/scripts.d/davescripts
```
#!/bin/sh
#
#scripts to take care of rt73 module and restart alsa-utils

[ -x /sbin/alsactl ] || exit 0

case "$1,$2" in
        suspend,*) ifconfig wlan0 down && modprobe -r rt73 ;;
        resume,suspend) modprobe rt73 && dhclient wlan0 && /etc/init.d/alsa-utils restart ;;
esac
```

I started with the alsa script from the same directory and modified it slightly to suit my purposes.

The command ```
/etc/init.d/alsa-utils restart
``` is in there because I had no sound after resume, and had to type that command after every suspend/resume cycle to get sound back.

Then, I made a link to the new script in /etc/apm/suspend.d and /etc/apm/resume.d

```
cd /etc/apm/suspend.d
sudo ln -s ../scripts.d/davescripts 50dave
cd /etc/apm/resume.d
sudo ln -s ../scripts.d/davescripts 50dave
```

Now suspend/resume works, and it reconnects to my wifi network at resume!

I won't go into how I [_set up serialmonkey drivers_]("http://ubuntuforums.org/showthread.php?t=400236"), or [_switched from acpi to apm_]("http://http://ubuntuforums.org/showpost.php?p=9953&postcount=3"), since those have been thoroughly covered elsewhere.

If you know a better/simpler(or simply another) way to take care of this, I would love to hear it!

---

