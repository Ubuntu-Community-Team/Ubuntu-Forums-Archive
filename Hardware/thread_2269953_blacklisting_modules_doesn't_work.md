---
title: "blacklisting modules doesn't work"
date: 2015-03-19
forum: Hardware
---

### Post by brennero on 2015-03-19
Hi,
I'm having this problem....I insert "blacklist ath9k" at the end of file /etc/modprobe.d/blacklist.conf,  launch "sudo update-initramfs -u", reboot....but the Atheros wireless card is still on ?!
I've tried with other modules and I've had the same problem...
In the past it worked for me....

Could someone help me ?

Thanks

Luca

---

### Post by dino99 on 2015-03-19
can you check that'ath9k' is the good typo when you run lspci ?

---

### Post by brennero on 2015-03-19
Thanks for your reply,
I've checked and the result is that it uses ath9k..


01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Wistron NeWeb Corp. Device [185f:3119]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0400000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at dfa00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k

---

### Post by dino99 on 2015-03-19
hm, could there be an other driver for that Atheros AR9485 ?

i've not read all the threads found on the net, but you might find what you need i suppose
[https://www.google.fr/search?q=linux+driver+Atheros+AR9485&oq=linux+driver+Atheros+AR9485&aqs=chrome..69i57.12324j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8](https://www.google.fr/search?q=linux+driver+Atheros+AR9485&oq=linux+driver+Atheros+AR9485&aqs=chrome..69i57.12324j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8)

---

### Post by brennero on 2015-03-19
if I give after boot : sudo modprobe -r ath9k the Atheros wifi disappear
I think the problem is properly the blacklisting...if can be useful I installed some new driver after through installing linux-headers-generic build-essential, perhaps modprobe make some confusion...
thanks

---

### Post by steeldriver on 2015-03-19
Do you have any stray modprobes that might be manually loading the module after boot up? such as in /etc/rc.local

---

### Post by brennero on 2015-03-19
thank steeldriver, 
I've opened /etc/rc.local and /etc/init.d/rc.local but I haven't found "modprobe" ....

---

### Post by Yellow Pasque on 2015-03-21
Perhaps another module (like ath9k_common) depends on it and loads it automatically.

---

### Post by jeremy31 on 2015-03-21
Show ```
cat /etc/modules
```
```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by brennero on 2015-03-21
you're right guys ! 

luca@luca-C22:~$ modinfo -F depends ath9k
ath9k_hw,mac80211,ath9k_common,cfg80211,ath

to completely remove ath9k and its dependies I added "install ath9k /bin/true" in /etc/modprobe.d/blacklist.conf and then # update-initramfs -u

thank you all for your time

---

