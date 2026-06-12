---
title: "Battery Issues - a never ending story (Lenovo Yoga 2 Pro, 14.04.2, Kernel 4)"
date: 2015-05-02
forum: Hardware
---

### Post by stefan_03 on 2015-05-02
Hey there,

I'm feeling desperate. My notebook came with Win 8.1, battery lifetime was 7-8 hours. I've installed Ubuntu 14.04, 4-4.5 hours (5 hours tops!). Well, I was researching and found this hint on askubuntu, including several comments: [http://askubuntu.com/questions/367963/ubuntu-on-lenovo-yoga-2-pro/389190#389190](http://askubuntu.com/questions/367963/ubuntu-on-lenovo-yoga-2-pro/389190#389190)

> [COLOR=#111111][FONT=Ubuntu]BTW, kernel 3.14 has got Haswell CPU support in intel_pstate cpufreq driver. This dramatically improves idle power consumption. I'm getting 10+ hours battery lifetime with 20% brightness
I've installed Ubuntu 14.10 (kernel 3.17 by default), and the battery life time increased to almost 6 hours. (which is still much less than on Windows, but a big improvement for a Linux machine)

So, I've researched again how to update the Linux kernel on the LTS 14.04 Ubuntu. 
[/FONT][/COLOR]http://www.linuxandubuntu.com/home/linux-kernel-4-0-rc1-released-install-in-ubuntu-linux-mint[COLOR=#111111][FONT=Ubuntu]

It worked fine, I've installed powertop and guess what - same problem as before. 5 hours battery lifetime are a bless! 

I don't know how Alexander G. from askubuntu managed it to get 10 hours battery lifetime. I've tried his optimization hints, but didn't really improve anything for me. But, unless he is a liar (which would make no sense to me), there has to be a way to improve battery life time on Ubuntu machines.

On Ubuntu 14.10 I had a discharge rate of max. 8-9 W, now it is at least 11! (right now 12.7W, 4.8W WIFI/network interface!) Due to the fact that 14.10 is only supported until June, I would like to use the LTS release.
Is there any way to get this done? Is there even a paid support for things like these? I am not a pro, and I cannot waste several hours in trying things that won't work for me. 

Thanks and have a nice weekend![/FONT][/COLOR]

---

### Post by stefan_03 on 2016-02-29
Almost a year later. If you read this and have the same issue: I get up to 6:30h battery time, which is really good. (normally 5-6hrs)
I set brightness to 30% auto (with xbacklight), installed tlp, powertop and I use Xubuntu instead of the Unity version. Current kernel: 4.2.0-30-generic
It's really much better than the 3.x kernel without tlp, it's at least 25% better battery time now.

---

