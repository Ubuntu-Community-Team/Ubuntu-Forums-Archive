---
title: "Overclocked or not?"
date: 2012-09-23
forum: Hardware
---

### Post by Skifu on 2012-09-23
Hi, i overclocked my i5 cpu from 3.3 to 4.5 GHz, however all possible sensors i have installed on ubuntu shows default 3.3 GHz...
I know its succesfully oc'd because when i dualboot to win 7, it shows the cpu is running @ 4.5.

So whats going on here? :o

U-12.04.1

---

### Post by jerrrys on 2012-09-23
I don't know whats going on, but here's some terminal commands to try:

cpufreq-info

sudo cat /proc/cpuinfo

sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

---

### Post by Skifu on 2012-09-23
Nope, according to those commands the cpu is running at stock (3.3 ghz) speed while working at 100 percent on all cores.
Is it possible that ubuntu "ignores" the oc profile, and just uses default speeds?
Tweaked everything in bios, so it shouldnt be dependent on the os.

---

### Post by jerrrys on 2012-09-23
OK, check these out

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379873](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379873)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=overclocked+cpu+shows+wrong+speed&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=overclocked+cpu+shows+wrong+speed&as_qdr=all&sa=Google+Search&lang=en)

---

