---
title: "Problem with Easycap (see video)"
date: 2011-11-01
forum: Hardware
---

### Post by pasquale.paletta on 2011-11-01
Hi, I've installed Easycap on Ubuntu 10.10 32bit.
Device is Dc60+, stk1160.
I can listen audio, but I get a "monoscope" with video after 3 seconds.

[http://www.youtube.com/watch?v=q2IWzGrqZQI](http://www.youtube.com/watch?v=q2IWzGrqZQI)

I hope this could help you to understand better.

Thanks.

---

### Post by emartinpulido on 2011-11-10
the same!
I've used Easycap on Ubuntu 11.10
Device is Dc60
I get the grey bar test after 3 seconds ,but  when I use Ubuntu 11.04 all goes well! :confused:

[http://www.youtube.com/watch?v=q2IWzGrqZQI](http://www.youtube.com/watch?v=q2IWzGrqZQI)

Help us, please!!!

---

### Post by Spitz on 2012-01-28
Same problem here, so a little bump...

---

### Post by Twinkel on 2012-03-19
I have this problem as well.  This is with the CVBS+S-Video version, using the RCA input on both ubuntu 11.10 with the standard driver and 10.04 with compiling and installing the driver myself.  Using a VCR, I can coax it back out of the "gray bars" state by pressing rewind and play alternately, but it doesn't last long in play mode before it goes back to "gray bars".  Interestingly, I think it will avoid the gray bars indefinitely as long as I'm rewinding or the VCR's blue menu screen is up.  As soon as actual video is playing, it will go back to gray bars in a moment.

Does anyone have a fix for this?  I'm kind of desperate.  Frankly, all I need is an inexpensive way to reliably capture maybe 1fps to be put on a web server before the end of April.

---

### Post by Twinkel on 2012-03-19
Oh, wait!  I've found this blog post:

[http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html](http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html)

which indicates that the "bars=0" option to the driver will fix the issue.  Indeed it seems to with my setup.  Best of luck!

---

