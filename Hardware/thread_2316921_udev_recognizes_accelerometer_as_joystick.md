---
title: "udev recognizes accelerometer as joystick"
date: 2016-03-12
forum: Hardware
---

### Post by zacklilly on 2016-03-12
I am attempting to get the accelerometer in my laptop to be recognized by gnome-settings-daemon so that gnome shell will change screen orientation. Right now the accelerometer is being recognized as a joystick and I am missing ***/lib/udev/accelerometer** and **/lib/udev/rules.d/61-accelerometer.rules** . *System information is below. How can I write a new udev rule and find the accelerometer binary?[I] 


```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
~$ uname -a
Linux Pollux 4.4.0-12-generic #28-Ubuntu SMP Wed Mar 9 00:33:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

```

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="ST LIS3LV02DL Accelerometer"
P: Phys=lis3lv02d/input0
S: Sysfs=/devices/platform/lis3lv02d/input/input9
U: Uniq=
H: Handlers=event8 js0 
B: PROP=0
B: EV=9
B: ABS=7

```

[/I]

---

### Post by davidedepau1996 on 2016-05-25
Hi, I have exactly the same accelerometer. I noticed those files have disappeared since Trusty. It's probably due to some update:

[http://packages.ubuntu.com/trusty/amd64/udev/filelist](http://packages.ubuntu.com/trusty/amd64/udev/filelist)
[http://packages.ubuntu.com/xenial/amd64/udev/filelist](http://packages.ubuntu.com/xenial/amd64/udev/filelist)

P.S.: give a look at /sys/devices/platform/lis3lv02d/position if you haven't already seen that ;)

---

