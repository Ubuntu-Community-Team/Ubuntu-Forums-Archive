---
title: "problem with my new server"
date: 2008-09-24
forum: General Help
---

### Post by S0VERE1GN on 2008-09-24
I have recently setup a server using the howto by ubuntuman001 and after setting up my net preferences to static I can no longer access the internet!  My ips match my router (its a netgear) and I tried ports 80 8080 and 8090. What else might be going wrong ?  Are there some settings I can change or check in webmin ?

---

### Post by russlar on 2008-09-24
is your dns set up properly? check the /etc/resolv.conf file for that. Also, you may need to manually set the gateway.

---

### Post by S0VERE1GN on 2008-09-24
> **russlar said:**
> is your dns set up properly? check the /etc/resolv.conf file for that. Also, you may need to manually set the gateway.

How do you setup your .conf file exactly? That must be the part I was missing. What info exactly are you supposed to put in there ?  And how do you go about manually setting the gateway ?

---

### Post by russlar on 2008-09-24
the resolv.conf file needs entries that look like this:

nameserver 4.2.2.2

also, the /etc/nsswitch.conf needs to have the hosts value include dns.


also, if you've set a static IP, trying sudo ifdown eth0, then sudo ifup eth0, where eth0 is your interface.

---

### Post by S0VERE1GN on 2008-09-24
thanks thanks! I got it to work connected via ethernet, can i get it to work wirelessly or is that out of the question? it would make my life a lot easier i am running a static IP.

---

### Post by S0VERE1GN on 2008-09-24
bump for helping me hook up the server wirelessly!!

---

