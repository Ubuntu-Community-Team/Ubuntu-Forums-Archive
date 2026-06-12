---
title: "Serial port speed for digital camera connection."
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2006-09-06
Right. I have this old digital camera, a Kodak DC210+. I wish to control it via its serial cable, using a program called [sdk]("http://www.tortuga.com.au/products/sdk/index.html").
(The key word here is **control**, I can read the card in my card reader if I want to.)
Whilst it works, I find that I can only connect at 9600, which means it takes 1.5 minutes to download a 640x480 picture.
According to [this]("http://www.tortuga.com.au/products/info/download_speed.html") page, 115200 should be achievable. They did it with a P166, I'm using an Athlon 800 here.

I found [this thread](http://www.ubuntuforums.org/showthread.php?t=51085) and tried that, but that didn't work:
```
chris@pollard:~/sdk-1.2.2/bin$ stty -F /dev/ttyS0 speed 115200
9600
chris@pollard:~/sdk-1.2.2/bin$ stty -F /dev/ttyS0 speed 115200
115200
chris@pollard:~/sdk-1.2.2/bin$ [COLOR="Red"]./status -p5 -s5[/COLOR]
Sep  6 09:34:19 status[9338]: lll     LOG   reset_camera_comms() failed ...
Sep  6 09:34:19 status[9338]: sdk     LOG   failed to reset camera comms
DC210_OpenCamera() failed
chris@pollard:~/sdk-1.2.2/bin$ [COLOR="Red"]./status -p5 -s1[/COLOR]
camera:             DC210 Zoom
.
. (removed for clarity)
.
zoom:               29mm
chris@pollard:~/sdk-1.2.2/bin$ stty -F /dev/ttyS0 speed 115200
9600
chris@pollard:~/sdk-1.2.2/bin$

```
Since the connection speed can be controleld by sdk itself, I think it overrides any change I make that way.

In the above sdk commands in red, -s1 = 9600 -s5 = 115200 -p5 = /dev/ttyS0

Any ideas how to speed it up a little?

---

### Post by xmastree on 2007-01-27
Bump...

Still trying to figure this out. I'm having the same problem with a different laptop.

Edit: Just tried it with pupppy linux, and it works up to 115200 but I can only get 9600 with ubuntu.

This is downloading one picture from the camera, at different speeds (set by the -s switch)
```
sh-3.00# ./dump -p5 -t1 -s1
dump: photos 1-1, port /dev/ttyS0, speed 9600, kodak dc210 zoom
dump: photo  1   0.926K/sec  100% complete  51K in 0:55 seconds
sh-3.00# ./dump -p5 -t1 -s2
dump: photos 1-1, port /dev/ttyS0, speed 19200, kodak dc210 zoom
dump: photo  1   1.815K/sec  100% complete  51K in 0:29 seconds
sh-3.00# ./dump -p5 -t1 -s3
dump: photos 1-1, port /dev/ttyS0, speed 38400, kodak dc210 zoom
dump: photo  1   3.549K/sec  100% complete  51K in 0:14 seconds
sh-3.00# ./dump -p5 -t1 -s4
dump: photos 1-1, port /dev/ttyS0, speed 57600, kodak dc210 zoom
dump: photo  1   5.209K/sec  100% complete  51K in 0:10 seconds
sh-3.00# ./dump -p5 -t1 -s5
dump: photos 1-1, port /dev/ttyS0, speed 115200, kodak dc210 zoom
dump: photo  1   9.789K/sec  100% complete  51K in 0:05 seconds

```

---

### Post by CoolHand on 2008-01-04
This is an old thread so you probably figured this out by now but I believe you are issuing the command incorrectly.  The term speed prints the current speed of the port:
stty -F /dev/ttyS0 speed
Returns the current setting.

Place the desired speed in place of the word speed to set a new speed:
stty -F /dev/ttyS0 9600
Sets port speed to 9600

Good luck.

---

