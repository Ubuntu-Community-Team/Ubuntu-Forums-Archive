---
title: "MiniPC with Intel 855GME display problem"
date: 2010-06-08
forum: Hardware
---

### Post by finesse on 2010-06-08
Hi, I have a Kingyoung MiniPC ([http://www.kingyoung.com.tw/S625.htm](http://www.kingyoung.com.tw/S625.htm)) the chipset they have chosen causes issues in windows and linux since it was intended for a laptop and assume there is always a laptop display present, when it's actually impossible.

Theres work arounds in Windows. I can only do text mode installs of Linux but as soon as it loads up the GDM Ubuntu defaults itself to the non-existent display (or so it seems as my VGA monitor gets no signal).

I installed 10.04 server on it and got everything setup over SSH, but thought id install the ubuntu-desktop so I could remote into it for extra benefits. As soon as I started the GDM via the init script the box locked up and lost all connectivity, and after resetting it continues to lock up on boot.

Thats where I am now, seems easy enough to fix, that's not why im posting though.

I don't need a GUI running locally (though that would be the best option), i've heard of being able to run an X session in a virtual display but would prefer a more conventional approach.

My first choice would be stopping Ubuntu from even seeing the non-existent laptop display, maybe via xorg? Im not too well versed with that though.

Any help would be very appreciated.

---

