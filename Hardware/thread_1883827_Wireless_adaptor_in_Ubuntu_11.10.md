---
title: "Wireless adaptor in Ubuntu 11.10"
date: 2011-11-20
forum: Hardware
---

### Post by sigma_z_1980 on 2011-11-20
I've upgraded to Ubuntu 11.10 from 11.04 yesterday. I'd like to install the wireless adapter, but the [advice]("http://ubuntuforums.org/showthread.php?t=1342593") I got the prevous time apparently doesn't work on the new version for some reason. Also, when I run 

```
lsusb
```

I get the result 

```
Linksys WUSB5GC...[RaLink RT2070L] 

```

although I'm quite confident on the previous version it was RT2870

any advice on how to solve the problem are massively appreciated.

---

### Post by mikewhatever on 2011-11-20
Here is a quote from the 'advise' thread:

> Ubuntu 11.10 "Oneiric Ocelot" no longer includes Ralink's out-of-kernel-tree drivers, instead it distributes drivers developed by the rt2x00 community project.

Looking through the advise itself, I've noticed that you had to blacklist the following:
```

blacklist rt2x00usb
blacklist rt2x00lib

```

I strongly suspect you might actually need them now, so try editing blacklist.conf and comment them out.
...like this
```

#blacklist rt2x00usb
#blacklist rt2x00lib

```

Then, try rebooting and see what happens.

---

### Post by sigma_z_1980 on 2011-11-21
I tried doing this, it didn't work. I also added

```

blacklist rt2870sta

```
but still nothing changed. Why did it set to rt2070 in the first place? 

> **mikewhatever said:**
> Here is a quote from the 'advise' thread:



Looking through the advise itself, I've noticed that you had to blacklist the following:
```

blacklist rt2x00usb
blacklist rt2x00lib

```

I strongly suspect you might actually need them now, so try editing blacklist.conf and comment them out.
...like this
```

#blacklist rt2x00usb
#blacklist rt2x00lib

```

Then, try rebooting and see what happens.

---

### Post by mikewhatever on 2011-11-22
Not sure really. Can you post the output of the following:
```
lsmod | grep rt2
```

---

