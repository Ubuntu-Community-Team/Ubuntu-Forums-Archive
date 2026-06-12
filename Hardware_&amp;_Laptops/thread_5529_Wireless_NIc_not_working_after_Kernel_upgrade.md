---
title: "Wireless NIc not working after Kernel upgrade"
date: 2004-11-19
forum: Hardware &amp; Laptops
---

### Post by kingnubian on 2004-11-19
Firstly, Ubuntu is simply an amazing piece of work and these forums are a model of how support and community should work.

I installed Warty and eaisly configured my wireless network card, based on the Atheros chipset, using the supplied Gnome "Networking" tool. All is well with wep running like a champ (I wish you could setup WPA from the same tool though).

I have Ubuntu running on an AMD 2500+ based system and decided to give the 2.6.8.1-3K7 kernel a try to take advantage of the specefic optimizations.

Now after doing so, installed it using synaptic, the wireless connection no longer works. When going to the Network tool I see that wlan0 is there but when I select it or try to start it the check mark goes away after a few seconds. Can I have some guidance with this please?

---

### Post by costoa on 2004-11-19
Could you post the results from ifconfig please?

---

### Post by randy on 2004-11-19
You may have to reinstall the restricted-modules package so it corresponds with your kernel version.

---

### Post by kingnubian on 2004-11-20
[QUOTE=costoa]Could you post the results from ifconfig please?[/QUOTE]

This is my ifconfig output:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:208059 (203.1 KiB)  TX bytes:208059 (203.1 KiB)


This is my iwconfig output:

lo        no wireless extensions.

sit0      no wireless extensions.


I have never seen "sit0" before.

---

### Post by kingnubian on 2004-11-20
[QUOTE=randy]You may have to reinstall the restricted-modules package so it corresponds with your kernel version.[/QUOTE]


That did the trick!!! Thank you very much. Obviously the "Restricted" modules were not installed with the kernel. Thanks again.....much appreciated.

---

