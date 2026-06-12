---
title: "Dell Inspiron 7559 - fans run constantly"
date: 2016-04-01
forum: Hardware
---

### Post by arnold_ziffle on 2016-04-01
I have a new Dell Inspiron 7559.  This has the newer skylake core i7.  It also has an nvidia 960m with optimus.

Under Windows 10 the laptop stays nice and cool.  The fans hardly come on, even under a load.  When they do come on, they shut off quickly and the temps drop.

Under Ubuntu (or any Linux I've tried), once the fans start, they run pretty much forever.  When the laptop is cold, and I boot into Ubuntu the fans are off.  However, after a few minutes as the laptop warms up, the fans will kick on and continue to run at the slowest speed.

Thinking since it's a newer skylake CPU, I've tried every Ubuntu mainline kernel (4.4, 4.5, 4.6rc1).  I've also tried Arch Linux, Manjaro, Linux Mint, etc.  The fans continue to spin.

**The one thing I did try that finally made the fans stop** was disabling the nvidia GPU with bbswitch, taking the bottom off the laptop to increase airflow, and opening a window in the room to lower the ambient temperature.   However the fans still run for about an hour once they start. Also watching the temps with lm-sensors, it seems like when the fans do shut off, it's when the SODIMM temp gets to 39c.  However, the 39c temp is never reached under -normal- conditions.  (i.e with the bottom cover on in a warm room)   CPU temps are always well below 40c when the fans are running.

I would assume there is some hardware issue, or something is heating up.  But then why does it work flawlessly under Windows?

So, anyway, I'm throwing this out there in case anyone has some thoughts or ideas.  I've pretty much exhausted all of my know-how and I am at my wits end.  

Help?

---

### Post by weatherman2 on 2016-04-01
Did you install Nvidia's latest driver for your video card?

---

### Post by arnold_ziffle on 2016-04-01
> **weatherman2 said:**
> Did you install Nvidia's latest driver for your video card?

Yes, tried that.  Tried with [COLOR=#111111][FONT=Consolas]nvidia-361 and [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]nvidia-364.[/FONT][/COLOR]

---

### Post by peter248 on 2016-05-13
This is not a HW issue. I have same laptop (i7 cpu) and same problem. (on Windows fans working just fine, after a while on idle they are off)
I've figured out that there can be seen fans speed in /sys/devices/virtual/hwmon/hwmon1 for dell device for kernel 4.4 (I've expected that fan control is managed by the BIOS out of the box, not by the kernel, but I was wrong obviously) 
Even CPU seems hotter on 4.4.0-22 kernel than on 4.4.10/4.6rc7.
In 4.6rc7 I can see the same behavior as on 4.4. What I found on internet is, that all the issues with the Skylake (hopefully with the cooling too) should be resolved by the 4.7 kernel so I/we have to be patient.

---

### Post by peter248 on 2016-06-11
Try to boot with grub parameter: acpi_osi="Linux"
Or try to play with pwmconfig setting, at least I could see it can control fans speed, but I did not manage to setup configuration for that.

---

### Post by peter248 on 2016-07-04
After lots of googling and trial-error attempts I have definitely solution for you.
install i8kutils
```
sudo gedit /etc/i8kmon.conf
paste:

[I]# Run as daemon, override with --daemon option
set config(daemon)      0

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose) 1

# Status check timeout (seconds), override with --timeout option
set config(timeout) 20

# For computer with 2 fans, use a variant of this instead:
# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
#set config(0) {{-1 0}  -1  47  -1  60}
#set config(1) {{-1 1}  36  61  50  70}
#set config(2) {{-1 1}  50  75  60  80}
#set config(3) {{-1 2}  65 128  70 128}

set config(0) {{0 0}  -1  55  -1  55}
set config(1) {{1 1}  36  60  36  60}
set config(2) {{1 1}  52  70  52  70}
set config(3) {{2 2}  65  78  65  78}
set config(4) {{2 2}  75 128  75 128}


# end of file
[/I]
sudo /etc/init.d/i8kmon restart
```

You can play with fan speeds and temperatures to get quietness as you wish, but this one is good for me :)

---

### Post by arnold_ziffle on 2016-07-12
Thanks for the update.  I had already played around with i8kutils a while back, but noticed that eventually the BIOS fan control re-asserts itsself.  Also, I kind of don't trust i8kutils on this laptop as it seems flaky.

I still think something is running hotter under Linux than under Windows.  If I pop the bottom off the laptop and blow cool air on the motherboard, the fans do shut off on their own. There seems to be an issue with the CPU getting into low power states under Linux, which may be the culprit.  You can see in intel powertop the CPU never gets into low power mode.   Apparently, there's an issue with power management on skylake CPUs in the kernel: [https://mjg59.dreamwidth.org/41713.html](https://mjg59.dreamwidth.org/41713.html)

Trying to get Linux to run properly on this laptop has been a miserable experience...

---

### Post by wildmanne39 on 2016-07-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by peter248 on 2016-07-19
Please to all you experiencing this bug with fans on Dell Inspiron 7559
there is a bug created 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1602888](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1602888)
So please click on the top-left: **This bug affects me** so more people report this and spread this bug link so it would be fixed sooner.

---

