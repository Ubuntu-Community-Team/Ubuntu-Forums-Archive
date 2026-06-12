---
title: "internet problems"
date: 2005-11-16
forum: General Help
---

### Post by Strongbad on 2005-11-16
Hi, I recently installed kubuntu 5.10 on my computer, and I can't seem to get an internet connection going. I have tried connecting using kppp, wvdial, and ppp, and they all appear to connect, but I can't load anything in my browser. 
Any ideas?:confused:

---

### Post by mlomker on 2005-11-16
[QUOTE=Strongbad]Any ideas?:confused:[/QUOTE]

I've never used a modem under linux, but you should be able to use **ifconfig** after connecting to verify that you have an IP address.  You could also try pinging something by number to see if you have a connection at all.  If it works by number but not by name then it's a DNS problem.

```

ping 209.98.65.80

```

Ctrl-c to stop.

then:

```

ping www.mpr.org

```

---

### Post by DDaland on 2005-11-23
Hmmmm, I"ve got basically the same problem- my external modem connects, but doesn't do anything once the Firefox is up

---

### Post by DDaland on 2005-11-23
BTW, just got my problem fixed (Sort off) in my Bios, disabled my built in network card- I"m now hooked up on line!!!! Now, have to figure out how to keep my network too.......

---

### Post by mlomker on 2005-11-23
Could be a default route issue.  Look at the output of **route -n** when they are both connected.  DHCP should update the routes when your dialup gives you an address, but maybe something isn't working right.

---

