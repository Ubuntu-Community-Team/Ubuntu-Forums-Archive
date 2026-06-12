---
title: "Wacom Intuos4 + Xorg.0.log + Ubuntu Karmic 64"
date: 2009-11-29
forum: Hardware
---

### Post by havnes on 2009-11-29
I have just converted my Thinkpad x61 to Ubuntu 64. I am a first timer, so there may well be a simple solution to my problem, though I don't know where to look.

My wacom tablet - Intuos4 - was discovered and runs like it is supposed to. Except that it fills my Xorg.0.log file with maybe 1 gigabyte of log data in a day. Gazillions of lines like this one:

<< Wacom Intuos4 4x6 - usbParse: dropping empty event for serial -1803342396 >>

This fills up the hard drive really fast. Things I have tried:

* Log rotate. I have put Xorg.0.log on daily log rotation, and retain just one copy. No help - the Xorg.0.log simply explodes while the Wacom pad is plugged in - fills up the /var/log partition before any log is rotated.
* Modifying xorg.conf - there are several tutorials on wacom+xorg. and all of them mention an xorg.conf file. But in Karmic there is no xorg.conf, instead there is a 'hal-based' approach (which I have found no documentation on).
* I studied this guide: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) (nothing mentioned about logging there) 
* Located the 10-linuxwacom.fdi file, nothing about logging there

Theories

* Is it possible to turn of logging to the Xorg.0.log file?
* Is it possible to configure the log level of the wacom pad?
* Is it possible to fix the error message "dropping empty event for serial -1803342396"

For the moment I just have to unplug my Wacom. I am thankful for any pointers.

---

### Post by dcsundr on 2009-11-29
Hi havnes,

I checked my own Xorg.0.log out of curiosity after reading your post, as it turns out I have this same behaviour and never noticed until now. For me it only occurs when I'm using the stylus or the mouse and so its not so serious as yours. In any case I passed this along to the thread dedicated to wacom tablets (URL: [http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)). Hopefully someone there can help get to the bottom of this.

In the meantime, it seems that Xorg.0.log is reset after a restart, so if you absolutely need your tablet maybe working after a fresh restart for a few hours and then restarting again might help... Sorry I can't be of more use.

---

### Post by havnes on 2009-11-30
Good to know there are ears listening. Thank you!

---

### Post by Favux on 2009-12-01
Hi havnes and dcsundr,

> Is it possible to configure the log level of the wacom pad?
There are two debug commands.  I don't know what the default level is but they can be set to 0.
>    DebugLevel    integer (0 - 12)         sets the level of debugging trace for the specified tool
   CommonDBG     integer (0 - 12)         sets the level of debugging trace for all tools 
				          associated with the same tablet.

In the .fdi you can use:
```
	<merge key="input.x11_options.DebugLevel" type="string">12</merge>
	<merge key="input.x11_options.CommonDBG" type="string">12</merge>
```
Setting the level you want of course.

> Is it possible to fix the error message "Wacom Intuos4 4x6 - usbParse: dropping empty event for serial -1803342396"
That may be something going on with the linuxwacom 0.8.4-1 wacom.ko (the usb kernel driver/module).  I wonder if that might be a bug fixed in a later version, say 0.8.4-4.  You could try compiling the newer driver and its wacom.ko and see if it helps.  See this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

