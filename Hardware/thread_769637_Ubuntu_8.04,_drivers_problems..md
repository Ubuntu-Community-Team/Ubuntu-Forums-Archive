---
title: "Ubuntu 8.04, drivers problems."
date: 2008-04-26
forum: Hardware
---

### Post by suarez.duek on 2008-04-26
Hi, I was very happy with my new ubuntu 8.04, and everything was working fine, but then I shut it down and now I have no drivers, no graphic acceleration, no audio drivers, no wireless, etc, but 1 hour ago everything was working perfect. I dont know what to do, I really dont wanna install everything again, because this could happend again.. If someone could help me! I 'll be very grateful!
More details, I use Ubuntu 8.04, in a Hp pavilion dv6700t, with nvidia gforce 8600M.

---

### Post by Yellow Pasque on 2008-04-26
More detail, please. Have you tried reinstalling your graphics driver?

For audio, please give me the result of these commands:
```
lsmod | grep snd
aplay -l
```

For your wireless, is the driver loaded and the chip connecting to your router? Please run:
```
sudo lshw -C network
sudo iwconfig
```

---

### Post by suarez.duek on 2008-04-27
thx for everything but is not just that, nothing is working now... i was wondering if there is any restore point or something like that, I been reading and i think there is not!
THX ANYWAY!

---

### Post by Yellow Pasque on 2008-04-27
What happens when you boot the system?

Are you able to boot into recovery mode? (Press 'Esc' to access the boot menu)

---

### Post by suarez.duek on 2008-04-27
I'm able to use my computer, I fixed the graphics, but a lot of others things are not working... I wonder why... When I boot my computer, everything seems to be normal... I think I might use feisty that works perfect for me. Yes I'm able to boot in recovery mode. Can I do something from there?

---

### Post by chek2fire on 2008-04-27
Try to download envyng from synaptic and install the nvidia driver from there

---

