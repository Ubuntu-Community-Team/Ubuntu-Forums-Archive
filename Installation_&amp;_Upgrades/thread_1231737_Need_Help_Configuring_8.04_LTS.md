---
title: "Need Help Configuring 8.04 LTS"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by shirato on 2009-08-04
Hello,

I recently decided to upgrade my Feisty Fawn and since 9.04 does not support my graphics card, I ended up installing 8.04 LTS. I was never very good when it came to using Linux and usually had people I could ask to help me set things up. In any case, I use a Radeon 9200 graphics card, K8 Triton Motherboard and an AMD 64 athlon Processor.

When I boot Ubuntu, I need to go to recovery mode and hit xfix followed by resume since GDM does not load with a regular start-up. My CPU is clocking at 99% all of the time and there is nothing listed when I go to System -> Administration ->Hardware Drivers.

Please help me get thhis working properly (have done sudo apt-get install xserver-xorg-video-ati and anything else I could find when searching the forums)

---

### Post by presence1960 on 2009-08-04
Try [EnvyNG]("http://albertomilone.com/nvidia_scripts1.html")
I don't believe it is in the hardy repos. if it isn't download from that link.

---

### Post by shirato on 2009-08-04
Thanks, that fixed my graphics problem. However my CPU is still working at 100%

---

### Post by shirato on 2009-08-04
After using the top command, I found out that Xorg was responsible. I changed the Visual Effects to None and it greatly improved. I wish there was another solution but this works for now.

---

### Post by presence1960 on 2009-08-05
> **shirato said:**
> Thanks, that fixed my graphics problem. However my CPU is still working at 100%

Disable Tracker (search indexer)

---

