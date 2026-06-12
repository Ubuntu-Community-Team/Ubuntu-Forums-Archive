---
title: "Laptop monitor stuck at 800x600 res!"
date: 2010-01-22
forum: Hardware
---

### Post by michael.wayne on 2010-01-22
Hi all,
I am having trouble with my monitor using Ubuntu for the first time. I have a laptop and the resolution of the screen is stuck at 800x600 (Monitor: Unknown).

I have been searching the forums and have come across a bit of code (I think it's code anyways) and it says it has to be added into the monitor section of the xorg.conf file. Thing is I cannot find the damn file!

I tried to 'locate' it, here are the results:
 	Code:
```
mike@mike-laptop:~$ sudo dpkg-reconfigure xserver-xorg
mike@mike-laptop:~$ locate xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
```
If anybody may be able to help that would be great!

 


Thanks,
Mike :confused:

---

### Post by l3git.h4cker on 2010-01-22
What version of Ubuntu are you running?

Have you tried the following:


Open up xorg.conf:

```

sudo nano /etc/X11/xorg.conf

```Change the " Modes   "800X600" " to fit your screen.
ex) Modes "1440x900"

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection "Display"
        Modes   "800x600"    <--------------------------- This is what you want to change.
    EndSubSection

```control-o then enter to save what you changed in nano.

When you are finished, restart Xorg with the control-alt-backspace command.
If that doesn't work, log off and log back in.

Hope this helps!:popcorn:

---

### Post by pi/roman on 2010-01-22
It sounds like you don't have an xorg.conf. Check your /etc/X11 folder to see if you have an xorg.conf:
ls /etc/X11

If not this will create one called xorg.conf.new:
sudo X :2 -configure

This will move it to your /etc/X11 folder and rename it to xorg.conf:
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf

---

