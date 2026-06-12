---
title: "CPU governor / speedstep problem or bug"
date: 2011-06-21
forum: Hardware
---

### Post by acidicX on 2011-06-21
Hi there,

I recently switched from Ubuntu Natty to Kubuntu Natty and I must say  after I switched from KDE4.0 back to gnome2/ubuntu because of severe issues, it  really improved and I really like 4.6.

There is, however, a big problem for me in the current release:
Since the CPU governor profile UI options were removed from 4.5 to 4.6  (how stupid was that? are we going the Apple way now, Novell?), you are left  with no choice but either to trust "something" inside KDE to select the  right governor, or to use cpufreq on the command line.

The first option does not work for me at all. KDE always loads the  "performance" governor profile and even sets the minimum clock to 2 GHz  (which is max for my Core2Duo T7300) which results in having the fan on  full speed all the time - which is pretty annoying.

No harm done, I thought, and just wrote a script:
```
sudo /usr/bin/cpufreq-set -c 0 -g ondemand -d 800;
sudo /usr/bin/cpufreq-set -c 1 -g ondemand -d 800
```which is loaded after login and with every energy profile switch.

Sadly, it does not work. KDE randomly switches the governor back to "performance".
I don't know when it does it, since I don't know any means how to track a program accessing the governor setting.
I would really like to get rid of this, I would have opened a bug report on launchpad but as I just explained I don't know which packet is causing this behaviour.
 I did **not** have this problem under Ubuntu natty, so I guess it is entirely a KDE related bug.

I would really appreciate any help to solve this.
Thanks,
acidicX

---

### Post by *nix* on 2011-10-22
Hi

Is the program  -  [COLOR=DarkRed]***freq-expert***[/COLOR]  -  for KDE, Gnome and other...  try the its

   [https://sites.google.com/site/freqexpert](https://sites.google.com/site/freqexpert)  -   official site

All the best!

---

### Post by diasf on 2011-10-22
customize your cpufreqd.conf ... that way the deamon will do your settings and you don't have to worry

(My laptop overheats by default - hp touchsmart tx2 - the only way to be able to use it decently is to properly configure cpufreqd. Even from liveCDs. But works like a charm, has tons of options and I don't have to worry with the processor going over 100C anymore)

---

### Post by *nix* on 2011-10-25
> **diasf said:**
> customize your cpufreqd.conf ... 


freq-expert has a graphical interface - GUI

[IMG]https://sites.google.com/site/freqexpert/home/freq-expert-u-01.jpg[/IMG]

---

