---
title: "Lenovo S10 can't change fan speeds"
date: 2008-10-28
forum: Hardware
---

### Post by CIement on 2008-10-28
Hi, I just finally got Ubuntu working after some partitioning problems, but now the problem I have is that I can't control my fan speeds. You see, the fan is pretty loud and it's really annoying to have to listen to it go on and off. I don't mind if it has to turn on when I'm running gpu/cpu intensive applications by all means, but when I'm just browsing the web or something and my cpu is still at 40 degrees I'd really rather have it off. This is especially the case when I'm in class.

Anyhow, I went to several how-to control fan speed guides that basically tell you to use apt-get to install lm-sensors and what not, but for some reason I can NEVER get the kernel modules to work.

I've used sensors-detect, had the code written automatically for me, and then used sudo modprobe on the modules it detected for me but still no luck; when I use "sensors" after that it still says that I need to run the necessary kernel drivers

if you must know, it told me that the necessary modules are lm75 and i2c-i801

Thanks for the help guys, hopefully I can get this working soon so I'll be able to bring my laptop to class.

---

### Post by CIement on 2008-10-28
bump

---

### Post by CIement on 2008-10-28
bump..

is it possible that my system is just not supported from lm-sensors?

beccause right now sensors-detect actually finds stuff but the only problem is that even after I use modprobe and put the given commands into "modules" when I run sensors or even pwmconfig I get an error saying that there are no sensors detected and it tells me to run sensors-detect.

if that's the case then it will probably be fixed if I just update to 8.10 right?

---

