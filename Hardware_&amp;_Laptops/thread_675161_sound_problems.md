---
title: "sound problems"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by sandclock on 2008-01-22
Hi i installed ubuntu 7.04 recently but i dont have sound i dont hear anything on pc. 
I ran command 
"cat /proc/asound/card0/codec#* | grep Codec" 
As i read in forums and i got output 
"Codec: Realtek ID 662" 
dont know what to do now
Regards
Nik

---

### Post by sandclock on 2008-01-22
Bump anyone?

---

### Post by Yellow Pasque on 2008-01-22
Try adding the following line into the /etc/modprobe.d/alsa-base file:
```
options snd-hda-intel model=3stack
```

Other models to try for your codec (like above but use the word in the left column after model= )

ALC662
-----------------
3stack-dig        -  3-stack (2-channel) with SPDIF
3stack-6ch       -  3-stack (6-channel)
3stack-6ch-dig -  3-stack (6-channel) with SPDIF
6stack-dig        -  6-stack with SPDIF
lenovo-101e    -  Lenovo laptop
auto                -  auto-config reading BIOS (default)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by sandclock on 2008-01-22
tried every solution in given in there still cant hear a damn thing :(
Any ideas guys?
Regards
Nik

---

### Post by Yellow Pasque on 2008-01-22
Did you restart each time?

---

