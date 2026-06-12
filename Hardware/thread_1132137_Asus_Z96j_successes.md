---
title: "Asus Z96j successes"
date: 2009-04-21
forum: Hardware
---

### Post by plysovej_kaktus on 2009-04-21
2.6.28-11-generic
Ubuntu 9.04-rc jaunty 

**ALI 5602 BISONCAM **is working on Asus Z96js

internet is full of howto's. After few hours of trying, i've tried this one:

[http://doc.ubuntu-fr.org/webcam_ali]("http://doc.ubuntu-fr.org/webcam_ali")

I've used NO patches anywhere etc.

```

modprobe gspca_5602 

```

in the beginning, it worked with mplayer, but broken and scratchy on v4l
screen full of broken "bitmap" green etc.

mplayer tv:// -tv driver=v4l:device=/dev/video0:width=320:height=240

then

```

apt-get install *v4l*

```

and maybe some i don't know exactly and reboot

it worked with xawtv smoothly and great

for skype: 
```

LD_PRELOAD=/usr/lib/libv4l/v4lconvert.so skype

```

mplayer ( but it still saying something about codec and not working ):
```

mplayer tv:// -tv device=/dev/video0:width=320:height=240

```

---

