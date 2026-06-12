---
title: "Brightness too hight and can not be changed on Desktop PC"
date: 2015-01-12
forum: Hardware
---

### Post by dixandreas on 2015-01-12
Hello,

I am have the problem that with Ubuntu Gnome 14.04 the brightness of the screen is too high (black color is dark grey).
Additionally, it can not be changed in the settings. Well, it can, but changing the slider has no effect.
As I am using a desktop PC, I do not have any function keys to control brightness.

I also have an Ubuntu 13.04 installed and with this version, the brightness is OK. Therefore, I think it is not a problem of the screen. However, changing the slider has also no effect in this version.
13.10 was the first version, where this issue has occured.

After some googleing, I found that for some people the boot options
> acpi_osi=Linux
acpi_backlight=vendor
i915.i915_enable_rc6=1
video=1920x1080-24@60
helped to solve the problem.
Unfortunately, nothing has any effect, except "acpi_backlight=vendor" which removes the brightness control slider as well as any entries in the /sys/class/backlight directory.
Speaking of this directory, there is a folder "acpi_video0" in it, containing the files for brightness control.
Using grep, it says:
> actual_brightness:30bl_power:0
brightness:30
grep: device: Ist ein Verzeichnis
max_brightness:100
grep: power: Ist ein Verzeichnis
grep: subsystem: Ist ein Verzeichnis
type:firmware
Changing the slider also changes these values, but not the screen brightness.
Accordingly, the command 
> echo 2 > /sys/class/backlight/acpi_video0/brightness
also has no effect.

What I also tried is upgrading my UEFI to the latest version and installing the latest Intel drivers using the Intel Graphics installier for Linux.
Lastly, I started Ubuntu with Unity on a live USB, but I had the same brightness issues. Therefore, I would exclude Gnome as the error source.

About my hardware:
Mainboard: Gigabyte GA-H87N-WIFI
CPU: Intel Core i5-4570S
RAM: G.Skill DIMM 4GB, DDR3-1600
no graphics card
Screen: AOC I2769VM, connected via HDMI

```
uname -a
Linux andreas-1404 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

If I missed anything, please ask.
I am kind of desperate and would appreciate any help!

---

### Post by Mike_Walsh on 2015-01-13
This might sound like kind of a silly question, but..... As you're running a desktop with a separate monitor, can't you adjust screen brightness via your monitor controls?

I've been running desktops for years, and this is the way that I always adjust mine; I never bother with the system settings. 

I can't understand why you're attempting to do this via software, when all monitors that I've ever come across usually have physical, hardware controls for brightness, contrast, colour, saturation, sharpness, etc., etc. Would it not be better to try these first?

Visit this site:-

[http://www.manualagent.com/aoc/i2769vm/owners-manual/download](http://www.manualagent.com/aoc/i2769vm/owners-manual/download)

and download it, then go to page 20 of the PDF Owner's Manual; you'll find the relevant information for your monitor controls.

Hope that helps.


Regards,

Mike. ;)

Edit: Having looked at reviews of your monitor, it appears to have a rather awkward menu system. Were you aware that your controls are tucked away right underneath the bottom edge of your monitor.....and that the markings for them are very hard to see, being marked in dark grey on a dark background?

---

### Post by dixandreas on 2015-01-15
Thank you for your response. 
I am aware of the monitor controls and the option to adjust the brightness with it. 
What bothers me is that when switching from 13.04 to 14.04, without changing any monitor settings, everything is brighter. And at the moment, I don't have any idea why.

Edit: 
Is it possible that this has something to do with a change between Xorg/wayland?

---

