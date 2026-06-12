---
title: "iPhone 4.2.1 Usual dbus error"
date: 2011-05-08
forum: Hardware
---

### Post by Daniel5 on 2011-05-08
Salutations!

So my iPhone 2G (Firmware 4.2.1) gets the usual dbus error when Ubuntu (11.04) attempts to mount it. Yes I've tried adding ppa:pmcenery/ppa to my repository sources list and upgraded via update manager but still to no avail. What else can I do?

Thanks bye!

---

### Post by Daniel5 on 2011-05-08
I where hunting this down for ages and eventually gave up. But resumed the chase today. Again after not finding any new fixes I made a thread here and as soon as I did BOOM! I find the solution.

For those who are still getting the dbus error this worked for me on Ubuntu 11.04 (don't know on different versions but should do). Open terminal and type

```
sudo apt-get install libimobiledevice2
idevicepair unpair
idevicepair pair 
idevicepair validate
```

And mount your happy iPhone!

---

### Post by alSee on 2011-06-08
> **Daniel5 said:**
> 
For those who are still getting the dbus error this worked for me on Ubuntu 11.04 (don't know on different versions but should do). Open terminal and type

It doesn't work. Got answer:
```
$ sudo apt-get install libimobiledevice2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libimobiledevice2

```

---

