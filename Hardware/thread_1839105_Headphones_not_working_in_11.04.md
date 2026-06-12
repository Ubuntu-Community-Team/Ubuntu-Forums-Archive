---
title: "Headphones not working in 11.04"
date: 2011-09-04
forum: Hardware
---

### Post by gbspnc on 2011-09-04
When I plug my headphones into my laptop, there is no sound. I know the headphones work and have tried using the PulseAudio controller to see if they somehow were muted but no luck. Any advice?

---

### Post by gbspnc on 2011-09-05
I've gone through the ubuntu sound troubleshooting with no luck as well. Anyone?

---

### Post by gbspnc on 2011-09-05
ALSA info. [http://www.alsa-project.org/db/?f=0e7448aaa4e4ae043d4cb9978ab4c3bc32a412dc](http://www.alsa-project.org/db/?f=0e7448aaa4e4ae043d4cb9978ab4c3bc32a412dc)

---

### Post by Antarctica32 on 2011-09-05
I had a similar problem once. 

[http://ubuntuforums.org/showthread.php?t=1784867](http://ubuntuforums.org/showthread.php?t=1784867)

Send a message to the guy who helped me asking for help, he knows what hes doing.

---

### Post by lidex on 2011-09-18
> **gbspnc said:**
> ALSA info. [http://www.alsa-project.org/db/?f=0e7448aaa4e4ae043d4cb9978ab4c3bc32a412dc](http://www.alsa-project.org/db/?f=0e7448aaa4e4ae043d4cb9978ab4c3bc32a412dc)

These are your options:
```
STAC9205/9254
=============
  ref           Reference board
  dell-m42      Dell (unknown)
  dell-m43      Dell Precision
  dell-m44      Dell Inspiron
  eapd          Keep EAPD on (e.g. Gateway T1616)
  auto          BIOS setup (default)


```
Add to alsa-base.conf using this format:
```
options snd-hda-intel model=xxxx
```
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

