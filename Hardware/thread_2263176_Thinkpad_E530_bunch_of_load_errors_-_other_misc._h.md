---
title: "Thinkpad E530: bunch of load errors - other misc. hardware"
date: 2015-01-30
forum: Hardware
---

### Post by gde061-www on 2015-01-30
Hello - I am about 3 months new to ubuntu, and generally happy with how much faster and more usable my "new" laptop is running without WIndows 8 (it litterally sat in on my desk collecting duest for most of  a year while I plodded on with an ancient desktop running XP, getting disgusted every time I turned it on with Win 8). Anyway, I did the normal install of 14.04 LTS from a CD I burned.  Everything that seems to matter appeared to work itself out in the install - I have wireless, bluetooth, and even the volume and brightness softkeys on the keyboard.  

However a few things don't seem to be "active":  (1) webcam - don't really care, but would like to know if it's possible to set it up. (2) Battery charging thresholds - to add longevity to the battery, the Lenovo power management interface for Windows used to let me avoid charging the battery.  (3) the fingerprint reader - was an automatic option for windows startup, but I know in earlier Thinkpads they had it available as a password that came up with the boot loader before you even got to the OS.  

Then there are the error messages that run by so fast I can't even read them every time the machine starts up.  I know one says to email somebody at lenovo who apparently tracks linux compatibility bugs.  Another says something about sockets failing to open.  

I'd love to hear from someone else who has an E-series thinkpad that converted to ubuntu about what they did?

Thanks!

---

### Post by gde061-www on 2015-02-02
Bump - simplified query:  I'm looking for (all for Thinkpad E-530)

1) Drivers for power management 
2) Drivers for webcam 
3) Drivers for fingerprint reader 
4) Instructions to guide me through finding the log where I see what the boot / startup errors are that run over my screen every time I start up.

Thanks in advance for the help...

---

### Post by mörgæs on 2015-02-08
The boot log can be seen with the command
```
more /var/log/dmesg
```
and 
```
more /var/log/dmesg | grep -i error
```
lets you search for 'error'. 

For getting help with the webcam it's best to post the output of ```
lsusb
```.

---

