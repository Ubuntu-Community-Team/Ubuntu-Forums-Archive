---
title: "Ondemand as default governor?"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by BrianB on 2005-10-29
Is it possible to set the ondemand cpufreq governor as the default one? Every time I set it as the governor it changes back to performance or userspace after a reboot. Any help?

---

### Post by bryan986 on 2005-11-03
I would also like to know how to do this, can anyone help?

---

### Post by bdaw on 2005-11-04
Hi. Here is my /etc/cpufreqd.conf

```
[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
pm_type=acpi
verbosity=5

[Profile]
name=ondemand
minfreq=800000
maxfreq=1800000
policy=ondemand

[Profile]
name=powersave
minfreq=800000
maxfreq=1800000
policy=powersave

[Profile]
name=performance
minfreq=800000
maxfreq=1800000
policy=performance

[Rule]
name=battery
ac=off
profile=powersave

[Rule]
name=battery_low
ac=off
battery_interval=0-10
profile=powersave

[Rule]
name=ac
ac=on
profile=ondemand

```

I had some problems with governors at my box so I had to add

```
cpufreq-powersave
cpufreq-ondemand
cpufreq-performance

```

into my /etc/modules file

So now with this I have following config
- when I'm plug in I use ondemand governor
- when i'm on batteries I use powersave

I have turion processor so it's good for me (on 1.8GHz my batteries last for an hour - on 0.8GHz they last for two hours...)

You can easily tune this for your own using "Rule" sections

After applying changes just do:
#sudo /etc/init.d/cpufreq stop
#sudo /etc/init.d/cpufreq start
to apply changes and use 
#cpufreq-info
or
#cat /proc/cpuinfo
to see what's going on.

Here is the best howto in this matter I found on the net
[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)

btw. I love gentoo comunity - the have really good howtos :)

Boleslaw

---

### Post by bryan986 on 2005-11-04
Thanks so much for this!

I replaced powernowd with cpufreqd, it is so much better, I love the config file and the chaning of states when plugged/unplugged!

---

