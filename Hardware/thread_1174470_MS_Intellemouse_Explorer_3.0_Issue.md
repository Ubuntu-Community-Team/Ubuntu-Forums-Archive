---
title: "MS Intellemouse Explorer 3.0 Issue"
date: 2009-05-31
forum: Hardware
---

### Post by rannday on 2009-05-31
Went through some guides on how to set up this mouse in /etc/X11/xorg.conf.

These guides also recommended installing this application titled imwheel .. I think. 

Well push come to shove, none of the guides worked out so well for me, my problem (which was having issues with mouse right-click acting funny: i.e. right clicking on desktop and automatically creating a new folder) has now become worse :

My scroll wheel no longer works. In Firefox it was acting as the previous/next buttons, quite annoying. And that is all it did. It no longer scrolls on anything. And still a lot of crazy right-clicking issues.

This seems to be another one of those issues, like my laptop's backspace button breaking, and becoming accustomed to shift-right arrow (replace) which is actually kind of quicker, that will grow on me (no more scrolling, which I am already used to working on a laptop so much recently since my desktop became unavailable to me because of some "faulty" duster)

So I went back and deleted the section in my xorg.conf file which help "their" information on how to set this up, but my problem still persists..

Any suggestions?

Thanks in advance!

-rann

---

### Post by cariboo on 2009-05-31
I find that Microsoft's mouse and keyboards are among their better products. I've been using an intelleemouse for years, and haven't had to set one up in /etc/X11/xorg.conf for about 6 years.

If your are using an old enough version that you still have to set the mouse type in /etc/X11/xorg.conf, then the mouse type you need to set is imps/2.

As of Intrepid, there is no mouse setting in /etc/X11/xorg.conf, it isn't needed any more.

---

