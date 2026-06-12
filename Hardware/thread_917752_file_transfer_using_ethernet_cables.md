---
title: "file transfer using ethernet cables"
date: 2008-09-12
forum: Hardware
---

### Post by Kevin Jones on 2008-09-12
Hello all,

I have installed HH on a dell xps. I also have a dell inspiron desktop with windows vista.
I am trying to transfer files via an ethernet crossover cable. I am looking for a set of instructions for how to set this  up. I have seen some instructions for doing this between vista and vista but there is very little on the web about this for linux (at least I can't  find it.)
If any    one has done this or knows of a good set of instructions can they help me?
I can do command line stuff, but itwould all be copy  and  paste because I don't   really understand it.
Thanks in advance
Kevin Jones

---

### Post by IntuitiveNipple on 2008-09-12
Assuming the cross-over cable works, you simply configure the interfaces on each PC with static IP addresses. Because it is a direct connection the sub-net will be a /30 (255.255.255.252) which allows the broadcast plus two IP addresses.

PC1:
```

sudo ifconfig eth0 10.0.1.1 netmask 255.255.255.252

```

PC2:
```

sudo ifconfig eth0 10.0.1.2 netmask 255.255.255.252

```

That should also create the correct entries in the routing tables of each PC.

If you want to address them by name add entries into each PC's /etc/hosts:
```

# set IF and PC correctly on each PC
IF=eth0
PC=1
echo "$(ifconfig ${IF} | sed -n 's/.*inet addr:\([0-9\.]\+\).*Bcast.*/\1/p') PC${PC}"  | sudo tee -a /etc/hosts

```

---

### Post by Kevin Jones on 2008-09-12
Thanks!!
I am kupgrading to kde 3.5.10 on my main  pc so I will  try this later this evening.
This  looks like a great way to connect my two pc's which both have ubuntu. I am not sure if the sudo commands given will work on vista. but I will check the settings on the vista laptop. 
Thanks once again.
btw... I  have a router and both pc's are on a linksys wireless system. I am guessing that the adjustments to the ethernet settings will  not affect the wireless config

Kevin

---

### Post by IntuitiveNipple on 2008-09-12
> **Kevin Jones said:**
> Thanks!!
I am not sure if the sudo commands given will work on vista.

](*,) no, probably not! I mis-read your original comment - thought it mentioned Dell XPs as in plural, not XPS :)

In Windows (obviously) use the GUI to configure it. Go to Network Properties, select the adaptor, choose the TCP/IP settings, change the adapter to Static IP address and use the values in my previous comment. You can ignore DNS and WINS settings.

You can edit the Windows hosts file in the same way; It is /Windows/System32/drivers/etc/hosts

---

