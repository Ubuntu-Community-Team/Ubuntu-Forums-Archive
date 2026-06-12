---
title: "Laptop speakers don't work after using HDMI audio out put"
date: 2012-06-26
forum: Hardware
---

### Post by themooking on 2012-06-26
Hi,

I'm using a an HP dv6 laptop with ubuntu 12.04. After switching to the hdmi sound output and then switching back, my laptop speakers don't work but headphones do. I looked around and tried altering my alsa-base.conf file, I added

options snd-hda-intel model=auto

This made the speakers work but they no longer turned off when I inserted my headphones into the jack (they did before). My theory is that since in the sound menu the 'digital output' option doesn't do anything and my headphones only work when 'speakers' are selected that the built in speaker/headphone bits in my laptop has its own system to switch in between headphones and speakers and that it has some how stopped working with ubuntu.

Has anyone had the same problem or have any ideas?

---

### Post by WataruS on 2012-07-08
The same to me, I can't find the way to make it turn back normal :(
Maybe I have to reinstall Ubuntu 12.04 T_T

---

### Post by Redblade20XX on 2012-07-09
Take a look into which master stream the system is set to. Also pulse audio volume control is something to look into for more information about what is happening.

- Red

---

### Post by themooking on 2012-07-09
How do I look into which master stream the system is set to? Should I install pulse audio or should it already be installed?

Thanks!

---

### Post by jmfal on 2012-07-09
I think RedBlade is referring to 

```
 pavucontrol      
```

It is not installed by default

Also open alsamixer and unmute the s/pdif controlS as they  are the volume controls for HDMI

---

### Post by americanman28 on 2012-07-12
go to sound setting and try to set a default output device

---

### Post by jmfal on 2012-07-12
Try
```
 sudo alsa force-reload      
```

Make sure speaker controls are unmuted and increased to 75 in alsamixer

play some music

---

