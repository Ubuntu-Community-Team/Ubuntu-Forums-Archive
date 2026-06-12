---
title: "[SOLVED] HP Tablet tc4200 Soft buttons"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by Andruk Tatum on 2008-01-20
I loaded Ubuntu on my HP tc4200, and I got everything to work except for the soft buttons, like the ink, rotate, Q, and presentation buttons.

I get keycodes from xev, and I can use xkeybind, but xkeybind-config does not work as well as it should.

Any help is greatly appreciated.

Andruk

---

### Post by Andruk Tatum on 2008-01-26
I used the drivers from here:

[http://chan.geekcamp.org/cgi-bin/tc4200forum/simpleforum.cgi?fid=02&topic_id=1191275510](http://chan.geekcamp.org/cgi-bin/tc4200forum/simpleforum.cgi?fid=02&topic_id=1191275510)

and xev picked up the buttons.  Just to let people know though,  it does something weird with the serial inputs (something about reordering the serial devices), as it is a bit difficult to get the tablet stylus and the soft buttons working together.  It is possible though, as a friend of miens (thanks dude) got it all working.

hopefully X.Org will get this thing straightened out soon enough so users dont have to do anything nifty.

Good luck to others who run into this problem.
-Andruk

---

