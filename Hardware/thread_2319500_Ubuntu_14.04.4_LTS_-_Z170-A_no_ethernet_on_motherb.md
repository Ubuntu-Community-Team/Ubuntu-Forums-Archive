---
title: "Ubuntu 14.04.4 LTS - Z170-A no ethernet on motherboard and no audio"
date: 2016-04-04
forum: Hardware
---

### Post by john541 on 2016-04-04
I have a Z170-A and I have no sound or ethernet.  I had to use an old  dusty WIFI card from my old PC to get on the Internet to troubleshoot.  I  have Ubuntu 14.04.

$ uname -r
3.13.0-83-generic



$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


How can I get my onboard ethernet and audio over hdmi to work?

---

### Post by john541 on 2016-04-04
fixed it by entering this command in terminal, although now I have wifi  and ethernet I don't have any network indicator in the upper panel, but  one of the network connections must be working for me to be able to post  this!



sudo apt-get install --install-recommends  linux-generic-lts-wily xserver-xorg-core-lts-wily xserver-xorg-lts-wily  xserver-xorg-video-all-lts-wily xserver-xorg-input-all-lts-wily  libwayland-egl1-mesa-lts-wily




this updates things to a new kernel, fyi

---

### Post by mörgæs on 2016-04-05
Thanks for posting. It seems like installing 15.10 would also have been an option.

Please mark the thread 'solved'.

---

