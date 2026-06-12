---
title: "GPU overheating with open source drivers"
date: 2013-04-30
forum: Hardware
---

### Post by pneuma00 on 2013-04-30
Hello all!

This is my first post here, hoping to get some help as I tried pretty much everything I could find on the internet related to my problem.

I have a HP pavilion dv6 laptop equipped with an ati mobility radeon 4650 gpu. I am using the open source drivers instelled by default since the AMD legacy drivers no longer support the kernel and X version of ubuntu 13.04, which I'm currently using.

I've been using ubuntu for a few months now and really like it; been having issues with overheating in 12.10 too.

i'd like to ask for some help, really anything that could help me with my overheating problems. My laptop is overheating when playing games, or even when watching movies. I'm using a program called lm-sensors to measure my temperatures. Sometimes, when watching a movie or playing for an hour or so, the temps would go up to 88 celsius, which I find quite unhealthy.

I tried setting the power_profile, located in /sys/drm/card0/device to mid, and even low, but it still overheats.

I'd really appreciate any kind of help, related to power management, reducing temperatures, modifying the system, the drivers, something.

Thank you all in advance.

ps. I have attached the lscpi and glxinfo output, hoping it will be useful.

---

### Post by Mark Phelps on 2013-05-01
You could try using Jupiter:  [http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html]("http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html")

---

### Post by 2F4U on 2013-05-01
Another option is TLP:

[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

---

### Post by pneuma00 on 2013-05-02
> **Mark Phelps said:**
> You could try using Jupiter:  [http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html](http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html)  Thank you, but isn't jupiter obsolete? I remember reading it on several forums and blogs.

---

