---
title: "Why can't flash detect my webcam"
date: 2010-02-25
forum: Hardware
---

### Post by josephellengar on 2010-02-25
I am running an eee PC 1005ha -- not the comp in my sig.  I am using karmic koala 32 bit and have flash version 10,0,45,2.  My problem is that flash tells me that it can't detect my webcam. I have used it with skype and other sources, so I know it works, but flash can't see it.  Does anybody have any suggestions?  Thank you.

---

### Post by Crafty Kisses on 2010-02-26
Now depending on what Flash sites you go onto that have webcam support, like for example Stickam, now Stickam can work, but there is a work around for it, but I haven't had much luck with webcams and Flash, what website were you trying to use, if you don't mind me asking?

---

### Post by josephellengar on 2010-02-26
> **Crafty Kisses said:**
> Now depending on what Flash sites you go onto that have webcam support, like for example Stickam, now Stickam can work, but there is a work around for it, but I haven't had much luck with webcams and Flash, what website were you trying to use, if you don't mind me asking?

[http://www.chatroulette.com/](http://www.chatroulette.com/) :oops:

---

### Post by wiljaxon on 2010-02-28
Hello I got my webcam working in Firefox (although this applies to Opera, Konqueror etc by substituting the application name as the last word):

Type this in your command-line console:

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

For Opera it would be:

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so opera

Worth a try for some types of webcam.

Will

---

### Post by secondstage on 2010-03-17
Does that command need to be executed each time I boot up or will my webcam now work forever and ever?

---

