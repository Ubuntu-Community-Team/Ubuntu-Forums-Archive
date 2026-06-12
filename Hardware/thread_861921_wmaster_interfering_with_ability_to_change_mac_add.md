---
title: "wmaster interfering with ability to change mac address"
date: 2008-07-17
forum: Hardware
---

### Post by saitoh on 2008-07-17
I used to use the following commands to change my mac address:
sudo ifdown wlan0 
sudo ifconffg wlan0 hw ether xx : xx : xx : xx : xx : xx
sudo ifup wlan0
However now in Ubuntu Hardy a generic(virtual driver?) device named wmaster0 also shows up in ifconfig. The problem is that when I change the mac of wlan0 and then try to reconnect to the network wmaster is still configured with my original mac address so I can't reconnect to the network.

Any help suggestions would be awesome.

(I tried to reconfigure wmaster0 with ifconfig and it doesn't work)

---

### Post by saitoh on 2008-07-17
Bump

---

### Post by saitoh on 2008-07-17
last Bump.

---

### Post by aleforum on 2008-11-09
> **saitoh said:**
> last Bump.

I am having the same problem. ](*,)

---

