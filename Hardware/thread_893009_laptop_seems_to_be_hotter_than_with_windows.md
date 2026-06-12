---
title: "laptop seems to be hotter than with windows"
date: 2008-08-17
forum: Hardware
---

### Post by kobacious on 2008-08-17
hello,

new to linux world.  switched from windows xp home to ubuntu 8, and since then my laptop seems to be generating more heat.  i have an older dell inspiron 6000 (bought around 2005?).  anyone else have this issue?  am i missing a driver of some sort or is this all in my head?  any help is appreciated.  thanks.

---

### Post by Ru$$i@N on 2008-08-17
my guess would be that your cpu frequency scaling is not enabled? :) that's at least the thing that i had. i've installed ubuntu 8.04.1 server edition (don't ask why) and i had to install powernowd, so the cpu runs at half capacity when not loaded.

HDDs give off a lot of heat too, so you might wanna look into the spin up or whatever it's called, sorry that i can't help you more

---

### Post by Yuki_Nagato on 2008-08-17
I know this carries some risks, but the benefits are large.

_[Hard Drive Stuff]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch05_:_Troubleshooting_Linux_with_syslog")_

It will save your hard drive, lower temp, among other things.

---

### Post by sdennie on 2008-08-18
By default Ubuntu doesn't enable all the available power savings features on a laptop so, it wouldn't surprise me if it generated more heat than Windows.  You could check [www.lesswatts.org](www.lesswatts.org) for how to enable these things as well as some of the links in my signature.

---

### Post by kobacious on 2008-08-20
thanks for the tips. much appreciated.

---

