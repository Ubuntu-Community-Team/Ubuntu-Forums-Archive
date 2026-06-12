---
title: "Broadcom BCM4318 Problem"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by blanc11 on 2007-01-07
After running the following commands

```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

I am able to get my wireless card to work, however does anybody know how I can get Ubuntu do to this at startup? Thanks.

---

### Post by drascus on 2007-01-07
hey there, 
I am so happy to help you with this as it took me days to figure out how to fix this. 
with the commands that you are using I am thinking that you read the article posted by compwiz. I think that I followed the same path that you did as well. here are somethings that are neccisary to the reboot that were not mentioned in that post. 

1) open up a terminal 

type: sudo gedit /etc/modules
add the line: ndiswrapper 
(this allows ndiswrapper to load at boot time)

2) at terminal 
type: sudo gedit /etc/modprobe.d/blacklist

add the line: blacklist bcm43xx
(this prevents the default driver from loading instead of the one you installed)

I just actually finished this whole process on my own computer and everything is working great. I hope this helps. if it does let me know. there might be need to start a wiki with all this information included. 
~mike~

---

### Post by blanc11 on 2007-01-07
Thanks! Its working! I already did the first thing, the second thing was the thing I was missing. Thank you so much!

---

