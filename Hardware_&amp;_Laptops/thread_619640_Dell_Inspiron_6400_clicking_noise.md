---
title: "Dell Inspiron 6400 clicking noise"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by Vladimir_BG on 2007-11-21
On some occasions under Linux my laptop makes weird clicking noise. I haven't been able to pinpoint it, but it seems to occur relatively random. Now, it may be that it's cause I always have 3-4 apps or more running, but makes me think it's linked to processes running. 
I haven't really figured out the pattern, but if you know something, please do tell!

My machine is:
Dell Inspiron 6400
Intel Core Duo T2300 1.66GHz
1.5 GB of RAM
Ati Mobility Radeo X1300

---

### Post by le N?KO on 2007-11-23
Would probably help.

i had similar problem with my inspiron 6400 having decent realtime performance for audio (was cracking hell), here what i done to fix it

1. edit the alsa-base file:
```
sudo gedit /etc/modprobe.d/alsa-base
```

2. then just add this @ end of the file
```
options snd-hda-intel position_fix=1
```

3. reboot, and it would be okey now.

(i have to add that i use the realtime kernel, maybe it fix it only with this kernel...)

---

