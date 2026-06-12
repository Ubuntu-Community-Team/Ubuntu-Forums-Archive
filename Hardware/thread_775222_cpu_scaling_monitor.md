---
title: "cpu scaling monitor"
date: 2008-04-29
forum: Hardware
---

### Post by rmx on 2008-04-29
hello

I've installed ubuntu 8.04 and the cpu scaling monitor applet stopped working.

Does anyone can help me?

thank you

---

### Post by rmx on 2008-05-02
anyone plase help me?

---

### Post by lamborghiniwang on 2008-05-02
what do u mean it stopped working?

---

### Post by leodp on 2008-05-02
Hi rmx,

how exactly did it stop? On which CPU?

I have an intel with Hyperthreading or so, that is recognized as 2 CPU, and it works. (scaling, freq. governor, actual freq. shown). I just did this steps:

sudo modprobe p4_clockmod

then add in /etc/modules the line
p4_clockmod
so that the module is loaded at boot



In case it does not work try also:
sudo dpkg-reconfigure gnome-applets 
and answer 'yes' to the question about the suid of the cpufreq-selector.

In case it still does not work try to reboot, or remove and add again the applet, so that it gets loaded with the new settings.

Ciao, Leodp

---

### Post by rmx on 2008-05-02
hello

thank you guys.

My laptop has a single core PIV mobile Dothan.

I'v followed your suggestions.

I've notice that now the cpu scaling applet doesn't display an error anymore. And the fan noise is much smaller. So I guess it is scalling.

I've notice also that now I only have two choosing modes (in ubuntu 7.10 I have 4) on applet.

However when I choose powersave mode it automaticaly jumps to performance mode.

so battery is running faster that on 7.10

any sugestions?

thanks

rmx

---

### Post by rmx on 2008-05-04
any suggestions please?

---

