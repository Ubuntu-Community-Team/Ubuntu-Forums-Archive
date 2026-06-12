---
title: "Kubuntu on Alienware 14 no eithernet recognized"
date: 2013-08-25
forum: Hardware
---

### Post by okos on 2013-08-25
Hello All,

I just bought an Alienware laptop and repartitioned for kubuntu. The first thing I noticed that the eithernet card is not working.

lshw shows :
> network UNCLAIMED
description: Eithernet controller
product: Atheros Communications Inc


ifconfig -a  shows:
> lo
wlan0

lspci
> Atheros Communications Inc Device e091 (rev 10)

I thought everything would work out of the box. Do I need to install the driver?

---

### Post by carl4926 on 2013-08-25
It'd be useful to see the network parts of

```
lspci -nnk
```

---

### Post by okos on 2013-08-26
OK will do. I am only going to post the eithernet part because I have to retype the output to another computer that has internet access. 

lspci -nnk
```

08:00.0 Ethernet  controller [0200]: Atherso Communications Inc. Device [1969:e091] (Rev 10) 
Subsystem: Dell Device [1028:05ac] 
0a:00 Network Controller [0280]: Atherso Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
Subsystem: Bigfoot Networks, Inc Device [1a56:2003]
Kernel driver in use: ath9k
Kernel modules: ath9k

```
Thanks in advance

---

### Post by carl4926 on 2013-08-26
I found a thread with similar issues
You might want to read it all.... [http://ubuntuforums.org/showthread.php?t=2035902&page=2](http://ubuntuforums.org/showthread.php?t=2035902&page=2)
Suggest you get a brew and put on a tin foil hat

---

### Post by okos on 2013-08-27
> **carl4926 said:**
> I found a thread with similar issues
You might want to read it all.... [http://ubuntuforums.org/showthread.php?t=2035902&page=2](http://ubuntuforums.org/showthread.php?t=2035902&page=2)
Suggest you get a brew and put on a tin foil hat

The issue is not wifi. Wireless works out of the box. The issue is the ethernet (No eth0 showing up in ifconfig). I switched cables with another computer and still no joy. I booted in windows 7 and there is no problem. The issue is with Kubuntu 12.04. I am a bit stumped in this.

---

