---
title: "Thinkpad trackpoint - sysconfig reset at boot?"
date: 2009-06-18
forum: Hardware
---

### Post by r1ch on 2009-06-18
Hello,
Is anyone able to help shed some light on this problem please?

I have used the configure-trackpoint utility from [sourceforge]("http://tpctl.sourceforge.net/configure-trackpoint.html") which has added two lines to my /etc/sysfs.conf file...

```
devices/platform/i8042/serio1/serio2/sensitivity=255
devices/platform/i8042/serio1/serio2/speed=131
```

This happens once I save my settings and click apply. The sensitivity of the trackpoint is adjusted and everything is great. I restart my machine though and once it boots up the original settings are restored. This is despite the fact that the file itself remains the same with both of the new lines in there.

Does anyone know why the trackpoint would revert back to its original settings despite the two new lines remaining in the file, or can perhaps point me the right way for further information please?

Many thanks for any help

---

### Post by oconnellda on 2009-08-23
Hey there. I have a Thinkpad T500 and I use the same program. I keep having the same problem myself. I don't mind changing the sensitivity on startup, but I would like to know if there is a way to permanently save the settings.

Also, I used this website to configure the scroll button:

[http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/](http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/)

So far, so good.

Thanks

---

### Post by Morientes on 2009-12-16
I have the same problem!
Anyone know how to solve it?

---

### Post by oconnellda on 2010-01-04
Taken from [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed)

This has worked for me. Basically, you can use the echo commands to adjust the sensitivity and speed. If you are happy with a certain setting, open terminal and:

sudo gedit /etc/rc.local

add the echo lines at the bottom. The details are below.

Sensitivity & Speed
Adjusting the speed and sensitivity of the TrackPoint requires echoing a value between 0 and 255 into the appropriate file. For example, for a speed of 120 and a sensitivity of 250, type the following into a terminal:

# echo -n 120 > /sys/devices/platform/i8042/serio1/serio2/speed
# echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity

Feel free to experiment with your settings until you find a combination that is comfortable.

When you satisfy your setting, add the two lines into /etc/rc.d/rc.local in order to avoid restoring the default setting every time the system reboots. In Ubuntu 9.10, add the lines to /etc/rc.local to avoid this.

---

### Post by zengfenfei on 2011-07-02
I have exactly the same problem.
Currently I execute the following commands to change the trackpoint sensitivity and speed every time I login to the desktop.
```

#set speed
sudo echo 255 > /sys/devices/platform/i8042/serio4/serio5/speed
#set sensitivity
sudo echo 255 > /sys/devices/platform/i8042/serio4/serio5/sensitivity

```

Anyone can tell me how to set trackpoint sensitivity and speed permanently?

I'm searching solutions on the Internet and find that /etc/sysfs.conf file may work. The contents of /etc/sysfs.conf:
```

#
# /etc/sysfs.conf - Configuration file for setting sysfs attributes.
#
# The sysfs mount directory is automatically prepended to the attribute paths.
#
# Syntax:
# attribute = value
# mode attribute = 0600 # (any valid argument for chmod)
# owner attribute = root:wheel # (any valid argument for chown)
#
# Examples:
#
# Always use the powersave CPU frequency governor
# devices/system/cpu/cpu0/cpufreq/scaling_governor = powersave
# 
# Use userspace CPU frequency governor and set initial speed
# devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
# devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 600000 
#
# Set permissions of suspend control file 
# mode power/state = 0660
# owner power/state = root:power

```

So I append the following two line the file, but it doesn't work.
```

devices/platform/i8042/serio4/serio5/sensitivity = 255
devices/platform/i8042/serio4/serio5/speed = 255

```

Maybe I don't set the mode and owner property, but I don't know how. Anyone can help out?
Thanks very much.

---

### Post by theicfire on 2011-08-14
I've got the same problem as well, changing /etc/rc.local doesn't seem to help either. One person mentioned changing /etc/rc.d/rc.local; is that right?

On 11.04:
chase@chase-ThinkPad-T61:/etc$ locate rc.local
/etc/rc.local
/etc/init.d/rc.local
/etc/rc2.d/S99rc.local
/etc/rc3.d/S99rc.local
/etc/rc4.d/S99rc.local
/etc/rc5.d/S99rc.local
/var/lib/update-rc.d/rc.local


Should I be making it or something?

Another curious point:

sudo echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity 
bash: /sys/devices/platform/i8042/serio1/serio2/sensitivity: Permission denied


But I can do that same command after "sudo su". Why is sudo not good enough, and is this part of the problem?

---

### Post by omghero on 2011-08-22
> **theicfire said:**
> I've got the same problem as well, changing /etc/rc.local doesn't seem to help either. One person mentioned changing /etc/rc.d/rc.local; is that right?

On 11.04:
chase@chase-ThinkPad-T61:/etc$ locate rc.local
/etc/rc.local
/etc/init.d/rc.local
/etc/rc2.d/S99rc.local
/etc/rc3.d/S99rc.local
/etc/rc4.d/S99rc.local
/etc/rc5.d/S99rc.local
/var/lib/update-rc.d/rc.local


Should I be making it or something?

Another curious point:

sudo echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity 
bash: /sys/devices/platform/i8042/serio1/serio2/sensitivity: Permission denied


But I can do that same command after "sudo su". Why is sudo not good enough, and is this part of the problem?

I also have same problems on ThinkPad E420s under Ubuntu 11.04. I tried almost all things which I found on the Internet, none of them works - after restarting, track point becomes slow again.

Does anybody know how to fix it?

---

