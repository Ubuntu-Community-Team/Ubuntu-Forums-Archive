---
title: "Toshiba L655D output jack disfunctionality"
date: 2011-09-23
forum: Hardware
---

### Post by geth022 on 2011-09-23
Heyo, i can hear my laptop's speakers fine, and they are working, however when i plug in a headphone cord, or an auxiliary jack, no sound is made to run through it, still playing loud and clear through the speakers. I would greatly appreciate some help in this manner. Just ask for alsa page w/ info on it if u need it, already up.

---

### Post by .... on 2011-09-23
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Hopefully, all jacks work properly after restarting system.

-- [http://askubuntu.com/questions/32956/headphones-phones-dont-work-on-my-toshiba-satellite-l655d-s5066-laptop](http://askubuntu.com/questions/32956/headphones-phones-dont-work-on-my-toshiba-satellite-l655d-s5066-laptop)

---

