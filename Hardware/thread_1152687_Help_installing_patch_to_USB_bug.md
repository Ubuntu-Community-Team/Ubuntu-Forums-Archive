---
title: "Help installing patch to USB bug"
date: 2009-05-08
forum: Hardware
---

### Post by Vostrocity on 2009-05-08
I need some help installing a patch so that I can mount my Sansa e260. The bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998"). A person called "Tim Kosse" (about 7 posts down) posted a patch and these instructions.
> Try these simple steps:

```
apt-get install build-essential devscripts
apt-get build-dep libgphoto2
apt-get source libgphoto2
wget http://launchpadlibrarian.net/25783305/libgphoto_sansa.diff
patch -p0 -i libgphoto_sansa.diff
cd libgphoto2-2.4.2
debuild -uc -us
cd ..
dpkg -i libgphoto2-2_2.4.2-0ubuntu4_i386.deb
```
After I type in the first line, it runs some lines of code, asks y/n about something (I chose yes), then it shows this.
[[IMG]http://img407.imageshack.us/img407/2451/screenshotandrewvostroc.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotandrewvostroc.png)
And I can't figure out where to go from there. :confused:

---

### Post by Ocxic on 2009-05-08
postfix is a mail server, something that i doubt you'll be using, so I would just leave the configuration unchanged.

---

### Post by Vostrocity on 2009-05-08
Well the thing is, the only thing I can do is scroll up and down. I can't select the menu options or ok.

---

### Post by Vostrocity on 2009-05-08
Bump..

---

### Post by Ocxic on 2009-05-08
use the tab key

---

### Post by Vostrocity on 2009-05-09
Wow thanks can't believe I didn't figure that out.

---

### Post by Vostrocity on 2009-05-09
Ok the first 5 lines went fine. And then I get to this
```

andrew@Vostrocity:~$ cd libgphoto2-2.4.2
andrew@Vostrocity:~/libgphoto2-2.4.2$

```
Is there anything I should do or do I just keep entering in the next couple of lines?

---

