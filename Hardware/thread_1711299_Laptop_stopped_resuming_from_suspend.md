---
title: "Laptop stopped resuming from suspend"
date: 2011-03-21
forum: Hardware
---

### Post by cyclopsface on 2011-03-21
Hello,

can anyone help me to diagnose why my laptop has stopped resumeing from suspend?  It goes to sleep ok but will not wake back up - it seems to be a video issue as sometimes the screen has colored stripes instead of being black during a failed resume.  It usually requires a hard restart (holding the power button) but sometimes I can switch to the first virtual terminal (ctrl-alt f1) and type (with the screen remaining backlit but black) my name and password and sudo reboot. 

I have an acer aspire one 741h with the poulsbo video chip. I don't know enough about Linux to narrow down the problem much - any help would be appreciated.
:popcorn:

---

### Post by cyclopsface on 2011-03-22
replying to my own thread in case this shows up in search engines.

1) I learned the relevant log file is /var/log/pm-suspend.log 

2) I solved my problem by moving 99video as described here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks)

the relevant command is: 
```
sudo mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video
```

---

