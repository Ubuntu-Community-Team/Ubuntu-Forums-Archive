---
title: "Realtek HD not working"
date: 2010-08-28
forum: Hardware
---

### Post by OddJoe69 on 2010-08-28
I am trying to get my realtek hd onboard sound card working. I have downloaded the drivers from there website and installed it, but now I have no sound at all. How do I fix this? I am needing my sound card working as I am a radio dj and my mic is a must as well. I was using windows and everything worked fine. But windows keept crashing, and when I called the computer manufacture they said it was built for Linux, and to use it. So here I am. This is the only issue I have had with linux so far. Any help would be great. Thanks in advance.

---

### Post by lidex on 2010-08-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by OddJoe69 on 2010-08-30
Ok I did that. Here is the link it gave me.

[http://www.alsa-project.org/db/?f=7998d6ed41386f067d7e05f6be39d6138f1d7de7](http://www.alsa-project.org/db/?f=7998d6ed41386f067d7e05f6be39d6138f1d7de7)

---

### Post by lidex on 2010-08-30
> **OddJoe69 said:**
> Ok I did that. Here is the link it gave me.

[http://www.alsa-project.org/db/?f=7998d6ed41386f067d7e05f6be39d6138f1d7de7](http://www.alsa-project.org/db/?f=7998d6ed41386f067d7e05f6be39d6138f1d7de7)

First try upgrading your alsa install using the link in my sig. Post your results.

---

### Post by OddJoe69 on 2010-10-02
bump

[http://www.alsa-project.org/db/?f=2d7759bfe4ed928ab0fed0e26d5b24f17425dd88](http://www.alsa-project.org/db/?f=2d7759bfe4ed928ab0fed0e26d5b24f17425dd88)

---

### Post by lidex on 2010-10-03
Yeah, didn't work. If you have alsa-backports installed, please remove them and run alsa-upgrade-script again. Then repost alsa-info. Be patient, we need to go step by step.

---

