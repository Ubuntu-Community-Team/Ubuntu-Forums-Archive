---
title: "network configuration on bootup"
date: 2005-11-28
forum: General Help
---

### Post by yib on 2005-11-28
Hi everyone,

Sorry if this has come up numerous times before, but is there a quick way of disabling network configuration on bootup? This is a real pain on a laptop, because it hangs there for a few minutes everytime i boot up because it can't find a network connection. Thank!

yib

---

### Post by linkunderscore on 2005-11-29
holy hell this is an annoying problem. It does this almost everytime I boot up my laptop because im on either hardwired or wifi--but it sits and thinks and attempts to configure the other network (i am obviously only ever connected to one at a time). 

Its VERY annoying. I would still like to run it at start up, but only if there is some way to configure how long it gets to think about it first.

---

### Post by erjohan on 2005-11-29
sudo  mv /etc/rcS.d/S39ifupdown  /

restart and see if it is disabled. To restore if it didn't work do:

sudo mv /S39ifupdown  /etc/rcS.d/S39ifupdown

Sorry for not giving a certain answer, it's just that it used to be called S??Network

---

### Post by lcg on 2005-11-29
[QUOTE=yib]
Sorry if this has come up numerous times before, but is there a quick way of disabling network configuration on bootup? This is a real pain on a laptop, because it hangs there for a few minutes everytime i boot up because it can't find a network connection. Thank![/QUOTE]
Have a look at ifplugd. It's a bit tricky to configure, but it only starts your interfaces when a connection is detected. A huge improvement for laptops.

HTH,
Lars

---

### Post by ozorba on 2005-11-29
[QUOTE=yib]Hi everyone,

Sorry if this has come up numerous times before, but is there a quick way of disabling network configuration on bootup? This is a real pain on a laptop, because it hangs there for a few minutes everytime i boot up because it can't find a network connection. Thank!

yib[/QUOTE]

There is a quick solution:

Just Ctrl-C when it is trying to connect to the network :-)

---

