---
title: "Ubuntu 9.04 hard drive runs hot"
date: 2009-06-26
forum: Hardware
---

### Post by caonima on 2009-06-26
Hi all,
I have this thinkpad T400 running ubuntu 9.04. The hard drive runs hotter than in windows xp. I used smartctl to see the temperature and load cycle count. The load cycle count did not increase in 30 minutes but the temperature increased 11 degrees. What could be the cause? Could it be the fan control? Now the temp is 42 degree.

---

### Post by Steelmourne on 2009-06-27
That shouldn't cause a problem. If temps go over 60 C, then its a problem.

---

### Post by caonima on 2009-06-27
The problem is that the heating does not happen in windows and it makes my palm uncomfortable.

---

### Post by ngine13 on 2009-08-23
i made a simple script in order to keep temp and load cycle count low :)

the main concept is that, by default, ubuntu boots with 

hdparm -B 254 /dev/sda 

command ([COLOR="Red"]edit when you are on ac and NOT on battery[/COLOR])

so after 15 min (900 sec) i change that to 253 and after 15 min again back to 254.. and this happens as long as ubuntu is running.

in few words i try to balance between "load cycle count" and relatively high temperature..

 

i saved it in /usr/bin as smarthd (i also made it executable):

#! /bin/sh

while (true)
do
sleep 900
hdparm -B 253 /dev/sda
sleep 900
hdparm -B 254 /dev/sda
done




and i put smarthd in /etc/rc.local in order to begin when ubuntu boots


the only problem is that i can't use tty1 anymore because the script is running on it (i think) - i don't know how to put it in the background - but this is not a problem anyway because i have tty2-tty6 to use :)

---

### Post by loomsen on 2009-08-23
Hello.

I had to suffer from the high load cycle / spin up retry count as well.

After one year working around I'm still not satisfied with the outcome.

setting apm to 254 causes too high temps and noise, apm=1 doesn't eliminate the bug, apm=128 neither.

These are the only three configurable steps for me.
See:
[[img]http://www.ubuntu-pics.de/thumb/22776/shot_20_dt35dC.png[/img]](http://www.ubuntu-pics.de/bild/22776/shot_20_dt35dC.png)

Are you able to set the value to 253? Or anything else than 1,128,254 and off?

---

### Post by ngine13 on 2009-08-23
yes.. 

my hd is a western digital scorpio 320 GB

in your case, in my script i would replace 253 with 128..

if with 128 your drive increases the "load cycle count" more than one (or two) per minute i would not use the solution i gave above.

my hard drive with 253 increases the "load cycle count" one per minute and with 254 none for ever (but temperature goes up to 53 celsius - it's hot in Greece this time of year.. :P )

i wish i helped.. :)

---

### Post by loomsen on 2009-08-23
> **ngine13 said:**
> yes.. 

i wish i helped.. :)

Well, not really, other than yet again confirming my hd to be crap ^^

I have a one liner setup in rc.local to take care of apm and my cpu undervolting settings.

Still I think I should simply go and buy myself a new hd. This is really annoying, and I've been investigating this issue really deep, toying around with all different kinds of settings, but still...

Btw, my HD is a
Device Model:     SAMSUNG HM250JI

---

### Post by ngine13 on 2009-08-23
i believe that your hard drive is not crap

crap is the way that hardware companies support linux :(

---

