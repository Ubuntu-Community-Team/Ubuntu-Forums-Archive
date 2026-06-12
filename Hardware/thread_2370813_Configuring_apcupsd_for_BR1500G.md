---
title: "Configuring apcupsd for BR1500G"
date: 2017-09-07
forum: Hardware
---

### Post by one.thing.done.well on 2017-09-07
[COLOR=#333333][FONT=sans-serif]I just got an APC BR1500G for my server and am trying to configure it with apcupsd, I've created a symlink of the UPS connection and put in the apcupsd config, I've set UPSCABLE to smart and UPSTYPE to apcsmart.  Currently when I run apctest I get
[/FONT][/COLOR]```

Checking configuration ...
sharenet.type = Network & ShareUPS Disabled
cable.type = Custom Cable Smart
mode.type = APC Smart UPS (any)
Setting up the port ...
apctest FATAL ERROR in smartsetup.c at line 155
PANIC! Cannot communicate with UPS via serial port.
Please make sure the port specified on the DEVICE directive is correct,
and that your cable specification on the UPSCABLE directive is correct.
apctest error termination completed

```
[COLOR=#333333][FONT=sans-serif]I'm using the cable that came in the box, which is USB to serial ethernet (I think), the model of the cable is 940-0127E.
[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Any help is appreciated[/FONT][/COLOR]

---

### Post by ergosteur on 2017-12-24
I have a BR1300G that I have working on Ubuntu 16.04.

in /etc/apcupsd/apcupsd.conf set:
UPSCABLE usb
UPSTYPE usb

Comment out DEVICE

Then run sudo apctest to test connection.

---

