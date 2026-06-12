---
title: "Lightdm: Black screen after suspend"
date: 2013-03-07
forum: Hardware
---

### Post by alaya.zied on 2013-03-07
hi,
I have recently upgraded my Ubuntu 12.10 to the Ubuntu 13.04 alpha to test it.
I'm doing all updates manually every day but I still have a little problem

When I suspend my laptop I get a black screen later and can't login.
The only output I can get is using a second monitor and go to command line interface whith alt-ctr+F1.

I tried this solution: deleting ~/.config/monitors.xml
I tried : sudo dpkg-reconfigure lightdm

but still have the same problem :/

---

### Post by wribeiro on 2013-03-08
Same thing here - HP Pavilion dv6000
GeForce 7150M / nForce 630M

---

### Post by gar onn on 2013-03-17
I found a solution here: [http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1130938/comments/8](http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1130938/comments/8)
It worked for me (on an device with intel)

---

### Post by alaya.zied on 2013-03-20
even after a fresh install I stil l have the same issue.
I have added a bug declaration here : 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1157628](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1157628)

---

