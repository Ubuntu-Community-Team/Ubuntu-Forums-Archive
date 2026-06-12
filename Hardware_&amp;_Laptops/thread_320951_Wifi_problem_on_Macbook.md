---
title: "Wifi problem on Macbook"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by dani_bcn on 2006-12-18
Hi all

I've a new install on a macbook and it's almost working, but I have problems with the wifi card.

The problem is that the wifi card is not showing. With a lspci I can find
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)

I've downloaded and installed the madwifi drivers from Internet and when I do a
modprobe ath_pci 
it loads all the modules but I can't find the ath0 card.
dani@macbook:~$ lsmod  | grep ath
ath_pci               101536  0 
ath_rate_sample        16512  1 ath_pci
wlan                  213052  2 ath_pci,ath_rate_sample
ath_hal               193104  2 ath_pci,ath_rate_sample

and in syslog I can see
Dec 18 14:31:11 macbook kernel: [17180614.628000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Dec 18 14:31:11 macbook kernel: [17180614.632000] wlan: 0.8.4.2 (svn r1860)
Dec 18 14:31:11 macbook kernel: [17180614.636000] ath_rate_sample: 1.2 (svn r1860)
Dec 18 14:31:11 macbook kernel: [17180614.640000] ath_pci: 0.9.4.5 (svn r1860)

My kernel version is:
Linux macbook 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux


Any idea how can I fix it?

Thanks

---

### Post by stereo on 2006-12-20
same here and i have still no solution for the problem. just to say, you're not alone ;o)

i just looked for the "wifi=on switch" on the enclosure...

---

### Post by RelativelyQuantum on 2007-12-31
> **dani_bcn said:**
> Any idea how can I fix it?

I'm not sure to be honest, as I am having the same problem. I've been all over the place looking for a solution, but with _absolutely_ no luck. I followed the guide here multiple times, but that didn't seem to do much:

[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

I don't know. I guess I'll keep trying. It's very discouraging, though, especially since neither my graphics card nor sound card will work. I'm dead in the water.

I'll run Leopard until I come up with something else; until then, good luck.

---

