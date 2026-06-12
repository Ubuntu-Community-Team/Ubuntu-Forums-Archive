---
title: "Wacom Cintiq 12WX on Ubuntu 11.10"
date: 2013-01-06
forum: Hardware
---

### Post by R-otrebor on 2013-01-06
Hi! i'm planning to purchase a Pen Display/Graphic Tablet Wacom Cintiq 12wX and would like to hear from you if i can configure it under my Ubuntu 11.10. I've already got a Wacom Bamboo running smooth on it, so i was wondering if a cintiq can also be easily configured.
Another option would be to update my ubuntu to version 12.04.1 LTS, but i would rather stay on the 11.10 as all my applications are running alright and there's always a risk when u update the version.
So what do u guys think?
Thanks in advance

---

### Post by tropt on 2013-01-14
I've been trying for 3days to setup my cintiq under ubuntu 12.10
to no avail.

No Tablet Detected

Macbook pro 10,1
cintiq 24hd

---

### Post by Favux on 2013-01-14
Hi R-otrebor,

Shouldn't be a problem in Oneiric.  You'll have to use a xsetwacom script because I don't think the Wacom tablet app. in Oneiric is up to the job.

Sample script attached to post #2:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
instructions on wiki page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)


Hi tropt,

Welcome to Ubuntu forums!

It should work out of the box in Quantal.  We'll have to do some diagnostics and see what is up.

By the way you are hijacking R-otrebor's thread and you should start a new thread for your topic.

Anyway on your new thread post the output, with the tablet plugged in, of the following commands:
```

lsmod | grep [Ww]acom
and
lsusb
and
xinput list
```
run in a terminal.

---

