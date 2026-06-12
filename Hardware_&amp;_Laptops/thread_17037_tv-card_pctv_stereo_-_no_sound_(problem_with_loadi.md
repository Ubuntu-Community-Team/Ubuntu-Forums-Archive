---
title: "tv-card pctv stereo - no sound (problem with loading modules)"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by Jakobo on 2005-02-25
Hello,

I've an Pinnacle PCTV stereo (saa7134 chip) in my box. The Card/Chip is detected just perfectly by the system as is the picture, I get from this tv-card.

But - my problem - the only sound I get in xawtv, motv or tvtime is white noise.

After googling around for several evenings: The problem is obviously the soundchip on the tv-card (tda8997) which is loaded by the system (listed in lsmod) but does not work in the right way. This problem occurs relativley often (on regarding the number of requests - even one in this forum). The (nearly nonexistant) answers, always mention to load the tda8997 with options. 
```
options tda9887 qss=0
```
As I'm a linux newbie I searched for the modprobe.conf mentionend in any of these answers to find out, that ubuntu doesn't have such a file. Instead it seams to use modules.conf (? Am I right ?) There I cannot find any line which is loading the tda8997, so I don't know where to put in this option. (When I just wrote it in the last line and rebooted, nothing did chang)

Where do I have to put this line in??

Greetings, Jakobo

---

### Post by Jakobo on 2005-02-26
Hello again,

today i got the tv-card working. When I reload the tda9887-module manually
```
$ rmmod tda9887
$ modprobe tda9887 qss=0
```
sound works just fine. But my problem with the modules.conf still remains: If I use the lines:
```
-r tda9887
tda9887 qss=0
```
in the modules.conf, the module doesn't load with the wanted option.
When I created a file called tda9887 in /etc/modprobe.d/

```
/sbin/rmmod tda9887
/sbin/modprobe tda9887 qss=0
```
I got error messages about invalid line 1 and invalid line 2 in the specified file.

So, my question is now: How can Iload the module with option from boot?

Greetings, Jakobo

---

### Post by Jakobo on 2005-02-27
Finally I found the solution for the problem.

I added the line in /etc/modules

```
tda9887 qss=0
```

The tv-card works now perfectly. :-)

---

### Post by r.stan on 2005-06-05
Hi Jakobo,

you just add "tda9887 qss=0" in /etc/modules ?

I tried this but still have the same problem  ](*,) 

thanks

stan

---

### Post by RDo on 2005-12-17
Hi,

I have the same problem... can't find a solution anyway.. please .. help.

---

