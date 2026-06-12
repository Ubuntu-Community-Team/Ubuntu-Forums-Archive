---
title: "On Aspire One, Wifi Issues"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Modred189 on 2009-01-19
SO I am trying to install Kubuntu on my Acer Aspire One. I got the OS installed and all updates are in. However, when following the instructions here: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
I get to the end of the first set of instructions (and nothing has happened in terms of pop-ups or alerts to new wireless card availability) and it says
"you may have to append ath_pci to /etc/modules"
Ok, so I need to add a text document to /etc/modules that contains the code that followed. But there is no such folder I could find. 
SO I did some digging and tried to make it by doing this:

```
cd /etc
mkdir modules
```

But it said it existed. wtf!?

---

### Post by Modred189 on 2009-01-20
Anyone?

---

### Post by niranjan on 2009-01-20
modules is the name of the file in folder /etc/
run 
```
sudo gedit /etc/modules
```
and append ath_pci at the end.

---

### Post by Modred189 on 2009-01-20
> **niranjan said:**
> modules is the name of the file in folder /etc/
run 
```
sudo gedit /etc/modules
```
and append ath_pci at the end.

I typed in 
```
sudo gedit /etc/modules
```

it asked for my password and spit out
```
sudo: gedit: command not found
```

---

### Post by timcredible on 2009-01-20
i think all i did was install linux-backports-modules via synaptic and reboot to get wifi working on my granddaughter's aspire one using 8.10. 

however, if you continue on with your steps, gedit isn't available because you're running kubuntu (kde window manager) instead of ubuntu which uses gnome.  gedit is a gnome app.  i don't know what editor kde uses, maybe someone else reading this thread knows?

---

### Post by neu2buntu on 2009-01-21
```
kate
``` is the default text editor in kubuntu,as far as i know. heres a post i did and it gets wifi working on ubuntu 8.10 on the aspire 1.,so maybe it will work in kubuntu also [http://ubuntuforums.org/showthread.php?t=1012973](http://ubuntuforums.org/showthread.php?t=1012973)

---

### Post by Modred189 on 2009-01-23
Thanks, trying now. I assume that I just replace gedit with kate on the instructions?

---

### Post by Modred189 on 2009-01-23
OK, big improvement, but for some reason the kubuntu network manager is acting weird and not letting me/giving me the option to enter my network key...

---

### Post by Modred189 on 2009-01-23
got it! Thanks!
After some fiddling in the network manager, it's up and running. Thanks so much!!!
(it ID's my network as having WPA encrption when it is actually WPA personal, whatever the difference is...)

---

### Post by neu2buntu on 2009-01-23
was offline there man,... glad u got it working, did u need the wifi fix in my post or did u sort it another way(this will be usefull to anyone folliwing this post)

---

