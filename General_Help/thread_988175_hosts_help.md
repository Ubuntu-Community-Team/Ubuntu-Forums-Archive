---
title: "hosts help"
date: 2008-11-20
forum: General Help
---

### Post by shcKr- on 2008-11-20
hey i am just after some help please, i had this set up before and then i moved the ubuntu machine which runs my LAN intranet server, this is my hosts file and all this used to work fine and now it doesnt :S
```
127.0.0.1	localhost
127.0.1.1	server
192.168.1.71 www.localdomain www

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

now on my windows machine i used to type 'www' into the address bar and it used to come up fine... now i do it and it just times out :S

im aware that when i moved it the ip changed, so i changed it in the host file also.
Another thing is that i can type 'www' in the address bar on the computer that is running the intranet and it will come up fine
sooooooo confused =(


Thanks in advance

---

### Post by cmnorton on 2008-11-20
Does your Windows system know about the new IP address either through its hosts file or through dns?

---

### Post by shcKr- on 2008-11-21
well on the windows computer, if i put 192.168.1.71 it brings up the intranet site fine :S
i just want to be able to put 'www' in the address bar and for it to bring up the same site as putting in 192.168.1.71

---

### Post by rampageoberon on 2008-11-21
can'y you just have the following removing the [www.localdomain?](www.localdomain?) ```
192.168.1.71 www
```

---

