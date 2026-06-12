---
title: "[HOW-TO] Set up Ubuntu with the TSC2007 Touchscreen"
date: 2011-09-04
forum: Hardware
---

### Post by abtekk on 2011-09-04
[CENTER][SIZE="3"]Setting up Ubuntu with a TSC2007 Touchscreen[/SIZE][/CENTER]

_Credits to Favux for the hours on end he spent helping me set up my touch screen._

OK, when you install Ubuntu (or Debian for that matter) and you have the TSC2007 touchscreen,
you will notice that it doesn't work straight out of the box, but luckily the needed driver
is still on the system, we just have to force Ubuntu to use it.

**_Step 1:_**
Get your terminal loaded up and type in the following command:
```

sudo apt-get remove xserver-xorg-input-synaptics

```
This removes the buggy synaptics driver that Ubuntu automatically assigns the device.

**_Step 2:_**
While terminal is open, type in this command:
```

sudo chown _username_ /usr/share/hal/fdi/policy/20thirdparty

```
(replace your username with the word username)
This is so we can create a file needed to get the touch screen working.

**_Step 3:_**
Download the 50-tsc2007.fdi file from here:
```

http://up.ht/ob1vPt

```

**_Step 4:_**
Once downloaded, place the file into the directory:
```

/usr/share/hal/fdi/policy/20thirdparty

```

**_Step 5:_**
Now reboot the system and you should now see that the touch screen operates the mouse :D.

You may notice that the calibration is slightly out so you must download the source code for
xinput_calibrator and compile it for your architecture.

Hope I helped!

---

