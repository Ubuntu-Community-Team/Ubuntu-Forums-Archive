---
title: "GIGABYTE DVB-T Hybrid TV Card GT-PTV-TAF-RH"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by Milos_SD on 2007-01-17
Hi, I will get this TV card soon. 

Can you tell me how to make it work in Ubuntu Dapper?

This is the chipset's for this card:

Tuner: Philips 8275A 
Decoder: Philips SAA7131E

Thanks.

---

### Post by orvils on 2007-09-03
I'm also intrested in this card. Did it worked/works?

---

### Post by Milos_SD on 2007-09-07
Yes, it works. 

You just need to make a tv.sh file in /etc/modprobe.d/
and add this in that file:

```
#!/bin/bash
rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=81
```

And make tv.sh script in your /home/USER/ directory to look like this:

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute
```

or

```
tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - 
```

The second script I discovered today, and I had a problem with it. So, I think that the first one is batter.

P.S. About first script to load module for TV card (/etc/modprobe.d/tv.sh :

When I use dmesg command, it says that the modprobe command is not usable (or something like that), but tv card is working. I think that you can put "option  saa7134 card=81" insted of that whole script, but I didn't tried that.

P.P.S. Sorry for my very bad english.

---

### Post by msaliba on 2007-12-09
hi i am new  linux 

i can not put the tv.sh file in /etc/modprobe.d/ folder it is read only in ubuntu 7.10 

can someone plz help 

thanks

---

### Post by Ice_cone on 2007-12-09
> **msaliba said:**
> hi i am new  linux 

i can not put the tv.sh file in /etc/modprobe.d/ folder it is read only in ubuntu 7.10 

can someone plz help 

thanks

yes, /etc/modprobe.d/ is a system folder, it's read only to avoid unauthorized modification
you can edit it in root (administrator)
open a terminal and type "gksudo gedit", enter what you want and save it in /etc/modprobe.d/

---

### Post by msaliba on 2007-12-09
THANKS YOU FOR YOUR HELP

i coped the tv.sh file to /etc/modprobe.d/

the other other one to my user folded i can not get tvtime to work

i do not understand what he means {P.S. About first script to load module for TV card (/etc/modprobe.d/tv.sh :

When I use dmesg command, it says that the modprobe command is not usable (or something like that), but tv card is working. I think that you can put "option saa7134 card=81" insted of that whole script, but I didn't tried that.)

do i use  modprobe command what do i put after it

---

