---
title: "Video tearing, Intel Mobile GM965/GL960"
date: 2014-09-01
forum: Hardware
---

### Post by d.vanheeckeren on 2014-09-01
Hi guys...Got some CRAZY tearing on ubutnu 14.04 with Intel Corporation Mobile GM965/GL960 graphics card.  I did follow the libsdl2 patch, but it does the same thing.  The weird thing is, ANY time flash runs, it's goes nuts.  Here's a video and two screenshots:

The video is at [http://www.youtube.com/watch?v=WGGc_FrgsLQ](http://www.youtube.com/watch?v=WGGc_FrgsLQ)
Screenshots are:
[http://www.teamrhino.info/files/1.png](http://www.teamrhino.info/files/1.png)
[http://www.teamrhino.info/files/2.png](http://www.teamrhino.info/files/2.png)

No additional drivers available that I know of in the repositories, all sources enabled.

---

### Post by d-cosner on 2014-09-01
That is really bad! Maybe this might help.

[http://www.omgubuntu.co.uk/2014/05/intel-linux-graphics-driver-installer-1-0-5](http://www.omgubuntu.co.uk/2014/05/intel-linux-graphics-driver-installer-1-0-5)

---

### Post by d.vanheeckeren on 2014-09-01
Definitely going to try that!  Back in a few minutes to let you know.  :o)  On a side note, everything else works fine unless it involves flash.  I've tried three different flash packages, including adobe's, but same result on all of them.  Anyhoo, be back in a little bit to let you know the results!  Thanks for taking the time to reply also!  :D

---

### Post by d.vanheeckeren on 2014-09-01
Thanks, d-cosner!!

You're awesome for being willing to help!  Here's what it looks like now:  [http://www.youtube.com/watch?v=B3zCwQ8oPqQ](http://www.youtube.com/watch?v=B3zCwQ8oPqQ)

I know the video looks a bit choppy, but that's because I was playing the youtube video and recording at 720p at the same time.  *LOL*  But it's nice and smooth now, I really appreciate it!

---

### Post by d.vanheeckeren on 2014-09-01
On the other hand...I do kind of like parts of the first video...very Max Headroom-ish.  *LOL*  But thanks again!

---

### Post by d-cosner on 2014-09-02
You can fine tune things a little more by turning off hardware acceleration in Firefox, it isn't supported in Linux anyway. Also, you can right click on a full screen flash video and turn off hardware acceleration in flash by removing the check mark. I do these tweaks on my system and flash works pretty decent.

Glad I could help!

---

### Post by d.vanheeckeren on 2014-09-03
I will do both of those next time I'm at my computer, which unfortunately won't be until tomorrow evening... But I really appreciate all the info.  For some reason, I never thought to check for Linux drivers from the manufacturer.  I guess Linux has me a little spoiled.  :D

---

