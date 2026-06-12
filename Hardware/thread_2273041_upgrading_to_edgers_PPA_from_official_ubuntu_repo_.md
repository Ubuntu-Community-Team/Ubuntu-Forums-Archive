---
title: "upgrading to edgers PPA from official ubuntu repo driver + nividia prime + indicator"
date: 2015-04-10
forum: Hardware
---

### Post by greatorety on 2015-04-10
I'm on **Ubuntu 14.10** with official ubuntu repo nvidia driver (nvidia-331-updates) and I'm currently using Bumblebee to have the discreet graphics card on my laptop (**Dell Inspiron 7537, GeForce GT 750M**) switched off (yeah, I know, then what do I need ubuntu nvidia driver anyway - well, that's how it is :)). 

Now, after some time using this setup I feel like gaming. So what I want to do is update the Ubuntu repo driver to the latest one from **the Edgers PPA**, switch from **Bumblebee** to **nvidia-prime** and add the indicator for an easy switching between cards. Did anyone perchance stumbled upon a comprehensive guide of how to accomplish this or maybe can instruct me briefly here what to do best and in what order?

---

### Post by dino99 on 2015-04-10
very simple: go for vivid, it works nicely and we are very close to final release. Chenge 'utopic' by 'vivid' inside /etc/apt/sources.list then update/upgrade but disable all third party repo first (ppa, ...)
vivid archive have the latest nvidia for your hardware and systemd works better than upstart do

---

### Post by greatorety on 2015-04-10
yeah, I'd definitely go for vivid, but thought I'd rather wait with it for the official release (only 2 weeks ahead)

---

