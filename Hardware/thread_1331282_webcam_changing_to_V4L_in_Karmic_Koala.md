---
title: "webcam: changing to V4L in Karmic Koala"
date: 2009-11-19
forum: Hardware
---

### Post by js31 on 2009-11-19
Hi,

unfortunately, ld.so.preload-manager isn't in the main repositories anymore, so the tutorial under [https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid](https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid) ("old webcam which doesn't work well with V4L2") outdated, at least relatively unexperienced users like me fear to break something.

perhaps someone here has a workaround for this, or hints/repository? without that configuration tool, many webcams like the Logitech S7500 won't work.

thanks in advance :)
J.

---

### Post by JohnnyJonJon on 2009-11-21
Yes please, i am looking for this too

---

### Post by js31 on 2009-11-24
yesterday, posted the problem at the Logitech QuickCam Team Forums, the URL is [http://forums.quickcamteam.net/showthread.php?tid=1041](http://forums.quickcamteam.net/showthread.php?tid=1041)

---

### Post by renkinjutsu on 2009-11-24
install the v4l-conf package ```
sudo aptitude install v4l-conf
```
and pass the -1 option to use it. Hope that helps

---

### Post by js31 on 2009-11-24
thank you =)

the setting is now 4vl. on [YT]("http://www.youtube.com/my_webcam"), a flickering preview, fine black&white lines, some mixed color dots

I got this output:
```
js@js-desktop:~$ v4l-conf -1
v4l-conf: using X11 display :0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown
skipping v4l2 (disabled on the cmd line)
/dev/video0 [v4l]: no overlay support

```

before that, tried
```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```

---

