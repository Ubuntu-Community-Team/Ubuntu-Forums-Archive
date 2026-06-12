---
title: "HOWTO::Mercury/Kobian TV Tuner Card"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by hellmet on 2006-05-27
HOWTO for runnin those cheap Mercury/Techcom tuner cards working
on Ubuntu...

EDITed for dapper

Open 'modules'

we need to load the tuner at startup

  gedit /etc/modules

Add this line at the end

> saa7134 card=3 tuner=39
tda9887 qss=0^for a Mercury/Techcom card
> saa7134 card=2 tuner=39
tda9887 qss=0^for a card that does not work properly with card=3(maybe problems
like no sound)

Dapper loads saa7134_alsa module by default..
We need to blacklist it (stop it from loading at startup)
```
gedit /etc/modprobe.d/blacklist
```add 
```
blacklist saa7134_alsa
blacklist saa7134
```to the end of the list..


Reboot..
I use TVTIME...so 
now in a terminal again,
```
tvtime-scanner
```Open TVTIME and njoy TV on ur computer...

I posted this..coz there are plenty of people
dying to get these crap tuners working..
And also if anytime I have diff. setting it up
on my comp. sometime later..I'll have a reference:mrgreen: 

Rock ON!!!

---

### Post by hellmet on 2006-10-25
edited for DAPPER... yea I know its been a late edit..
but ..I am lazy u know

---

### Post by hellmet on 2008-06-21
This HOWTO works perfectly even on Hardy Heron !! Just installed Hardy on my old computer!

---

