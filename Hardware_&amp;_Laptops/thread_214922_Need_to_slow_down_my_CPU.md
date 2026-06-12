---
title: "Need to slow down my CPU"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by shazbot on 2006-07-13
When on battery I would like to slow down my CPU, the CPU Frequency scaling monitor say I acnt do it,

Have installed Cpufreqd and cpufrequtils, but this hasnt changed anything

any ideas please

---

### Post by timetunnel on 2006-07-13
I've got an IBM Laptop and I've done it with the powernowd. Don't have the details right now because I'm at work (no Linux here). Can post details later.

---

### Post by shazbot on 2006-07-13
Have installed powernowd;, but haven't got a clue how it works

---

### Post by timetunnel on 2006-07-13
This may or may not work for your system:

First check that the powernowd propertly installed and running:
```
pstree | grep powernowd
```Should print "powernowd".

As super-user, create a textfile called "powernowd" in directory "/etc/default"

It must contain a line like this:
```
OPTIONS="-q -m 2 -l 40 -u 90 -s 100000"
```
You may have to fiddle around with the parameter for -l, -u amd -s, because these are for my system. They are explained in
```
man powernowd
```
To see the current frequency of your CPU you can add an applet to the panel, if you haven't done already.

---

### Post by djoelsson on 2006-07-13
Hi,

What processor do you have?  Are you sure it's capable of scaling the clock speed?

I have just bought a new core duo and battled with this for a long time.  I have a few hints for you, but like the post above, I'm at work, so I don't have my laptop available here.  I'll get back to you tonight.

Dan

---

### Post by timetunnel on 2006-07-13
You're right, I completely forgot to say that: I've got a Intel Pentium Mobile in my IBM Thinkpad. Quote from [http://www.thinkwiki.org](http://www.thinkwiki.org)

> powernowd originally was only written for AMD CPUs which support PowerNow! technology, but it supports other CPUs as well.

More details on the homepage of powernowd:
[http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html)

So it may or may not work for you.

---

### Post by djoelsson on 2006-07-13
No, it runs ok.

Basically, what I have done is install the speedstep-centrino module and then change both processor cores to the "ondemand" power governor and it seems to work well.  It scales to my lowest available frequency when I'm at idle and increases under load.  

I'll post the details of how to do it tonight (or you can try searching the forums, I found everything I needed here).

Dan

---

### Post by shazbot on 2006-07-13
I am running a amd Turion 64, I can change the speed if I boot in windows so thereofore I waould think that I do it in linux ...

pstree | grep powernowd
have tried this in terminal but nothing happens

---

### Post by djoelsson on 2006-07-13
shazbot,

Try:  
[I]
sudo /usr/bin/cpufreq-selector -g ondemand [/I]

That should put your processor in "ondemand" mode which scales with need.

If that works, install sysfsutils and add the following line to your /etc/sysfs.conf file

[I]
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand [/I]

FYI I have an intel processor so it might now work for you.  I also doesn't work any more in the latest kernel update 2.6.15-26-686,so I have to use 2.6.15-25-686.

Also, it may not work until you run in battery mode!  

Good luck!

Dan

---

