---
title: "Power history not functional with UPS?"
date: 2008-06-06
forum: Hardware
---

### Post by ijustam on 2008-06-06
Just had a power out for about 10 minutes, UPS kicked on and Ubuntu saw it and did so accordingly.  Saw discharge and did as it should, except my power history has no history, at all.

Is a UPS not measured on power history?

---

### Post by Tim Watson on 2008-06-08
It doesn't seem to be. Also the shutdown doesn't appear to work for me either. The history problem has been logged as a bug with gnome, and I've also opened a bug for the lack of shutdown problem:

[http://bugzilla.gnome.org/show_bug.cgi?id=516392](http://bugzilla.gnome.org/show_bug.cgi?id=516392)
[http://bugzilla.gnome.org/show_bug.cgi?id=537107](http://bugzilla.gnome.org/show_bug.cgi?id=537107)

---

### Post by ijustam on 2008-06-08
Awesome, thanks!  I was unaware of the shutdown bug, that could have had bad consequences if my power had been out much longer. :(

---

### Post by Tim Watson on 2008-06-08
Thanks. It seems that for my UPS (APC Back-UPS ES 700), the advice is to use apcupsd to control it but it would seem to be sensible to use the power management that's integral to gnome. It's just a pity that it doesn't seem to work!

For non-APC UPSs, NUT seems to be the best choice until gnome power manager is fixed (from what I've read, gpm might be using NUT but I'm not sure).

---

### Post by ijustam on 2008-06-08
I have an ES 500 and never got apcupsd to work.  I kept getting connection errors and never bothered to troubleshoot.

---

### Post by Tim Watson on 2008-06-08
I'll definitely delay trying that then - let's hope that there's some response from the gpm developers. I grabbed the source code from their repo but a two-minute skim didn't immediately show me where the problem lies. If there's no response in a few days I'll have a closer look.

---

### Post by ijustam on 2008-06-08
I just tried playing around with apcupsd some more...

My UPS sits in /dev/hidraw1: [   35.791557] hiddev96hidraw1: USB HID v1.10 Device [APC Back-UPS ES 500 FW:801.e5.D USB FW:e5] on usb-0000:00:1d.0-2

Doing the recommended manual advice in my apcupsd.conf...

```
UPSTYPE usb
DEVICE
```

and even

```
UPSTYPE usb
DEVICE /dev/hidraw1
```

nets nothing: ```
apcupsd FATAL ERROR in linux-usb.c at line 604
Cannot find UPS device --
```

[This post]("http://ubuntuforums.org/showpost.php?p=4282701&postcount=35") seems relevant, but following those steps had no positive gain.

---

### Post by Tim Watson on 2008-06-08
The post you link to does seem to have followed the standard setup as per the apcupsd web documentation. Rather than confuse the issue by installing apcupsd on my machine, I'll wait to see whether the gpm developers come up with anything. If not, I'll try installing and configuring apcupsd and I'll also look through the gpm source. I'll have to learn about hal and dbus first, though!

---

### Post by Tim Watson on 2008-06-10
I installed apcupsd and configured it as per the instructions (cable and type usb, blank device in /etc/apcupsd/apcupsd.conf and ISCONFIGURED=no changed to yes in /etc/defaults/apcupsd). It works perfectly for me, shutting down the machine at the right time and also powering off the UPS. Everything comes back up when the power returns.

---

