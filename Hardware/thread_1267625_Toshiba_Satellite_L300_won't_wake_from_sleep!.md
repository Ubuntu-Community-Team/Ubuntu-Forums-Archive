---
title: "Toshiba Satellite L300 won't wake from sleep!"
date: 2009-09-16
forum: Hardware
---

### Post by irrdev on 2009-09-16
I have a new Toshiba Satellite Laptop L300 on which I have just installed Kubuntu. All aspects of the OS work perfectly, including graphics and hibernation, except the all-important sleep feature. The laptop will properly go to sleep, but on "wakeup" I am immidately presented with a black screen; no messages, boot screen or output at all. Listed below is my system setup:
> Kubuntu 9.04 AMD64 with KDE 4.3 installed from Karmic backports
Intel Centrino Core 2 Duo Processor
Mobile Intel 4 Series Express Chipset Family (HD capability)
4GB RAM
I haven't tried Ubuntu on this laptop, but I would prefer to stick with KDE 4.3. Thanks in advance for any help or advice; without the sleep function properly working, I may have no choice but to use (ugh!) Windows 7... that would really be a shame, as all of my other computers use linux. :)

---

### Post by Dark_Stang on 2009-09-16
This may sound dumb but... don't use sleep? I tell at least 10 people a month the same thing. Sleep problems aren't just specific to Linux, XP, Vista, and 7 all have sleep issues as well. Actually... OSX is probably the only OS that tends not to have sleep problems.

If you're really wanting to trouble shoot it, see if you can get to a command line and try to restart kdm. Sleep, come out of sleep, press Ctrl+Alt+F1 and see if it dumps you to command line. If it does, press Ctrl+Al+F7 and see if you can get back to a GUI. If it doesn't, go back to the command line and run...
```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start
```

---

