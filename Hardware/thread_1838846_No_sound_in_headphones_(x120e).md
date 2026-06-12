---
title: "No sound in headphones (x120e)"
date: 2011-09-04
forum: Hardware
---

### Post by tech_girl on 2011-09-04
I installed ubuntu 10.10 on my Lenovo x120e recently with the x86_64 version. I have sound on the internal speaker but not when I plug in the headphone. I tried changing the configuration file according to online guides but still cant get the sound in my headphone to work. 

Here is info on my chipset:
```
http://www.alsa-project.org/db/?f=0e34110e7e69f572613a1cb4985fabf369f61795
```

Thanks.

---

### Post by .... on 2011-09-04
Try:
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
sudo /usr/sbin/alsa force-reload
```

---

### Post by tech_girl on 2011-09-05
> **.... said:**
> Try:
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
sudo /usr/sbin/alsa force-reload
```

Still no sound in headphones.

---

