---
title: "Internet problems after server upgrade"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by mbyrn1 on 2009-10-04
Hey,

I have some experience but for the most part I am new. I have had a amd64 version of ubuntu server (9.10) running with a web server mostly used for Torrentflux.

Everything was good until I decided to update and UPGRADE it with apt-get. For the most part there was nothing wrong but I had to change the grub back to normal and one other major thing....

The server uses a static IP from my router and that still works fine. The problem is that it cannot connect to the internet for some reason. I know it gets the static IP fine since I can still ssh from my regular desktop computer into it. I can access the torrent flux web page locally from within the LAN but it cannot connect to any seeds or search any torrent pages. Also I cannot ping anything outside of the LAN. I checked the eth0 settings and they are the same so it still gets the 192.168.1.127 static IP I set it up with a while ago.

Any ideas??

---

### Post by Dusal on 2009-10-05
Same problem here. Ubuntu Desktop x86 9.04 upgraded 9.10. can't fixed yet.
Although

/etc/init.d/networking restart

is temporary fixing. And after reboot problem will there. (Sorry for my english is poor.)

---

### Post by mbyrn1 on 2009-10-05
I ended up making eth0 dhcp instead of static and that fixed it but it used to be ok with static ip. Any ideas why an upgrade would start causing problems?

---

