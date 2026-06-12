---
title: "Lenovo X61 -- Wireless Completely Gone"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by skier on 2008-01-23
I plugged my X61 into an ethernet port a few weeks ago and now wireless internet is completely gone.  

Can anyone walk me through getting this fixed?

Previously I was connecting using eth1 which is now gone.

```

comp@ME:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```

comp@ME:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:C8:00:B3  
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fec8:b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1283672 (1.2 MB)  TX bytes:203764 (198.9 KB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by mbsullivan on 2008-01-23
Hi Skier,

Perhaps your wireless kernel modules got unloaded?  When this happens to me, I normally use the "load" script associated with the iwlwifi package that I used to get my wireless drivers (more on this later). However, perhaps just loading the correct modules will work for you. First, try:

```
modprobe cfg80211 && modprobe mac80211 && modprobe iwl3945 && modprobe iwl4965
```

And then see if "wlan0" appears in the output of "iwconfig". If the answer is "yes", then you should be able to connect to a wireless network the same way you always do.

If the answer is "no", perhaps you should try the latest Intel Linux drivers, and use the "load" script like I do.  Get the [newest snapshot]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.23.tgz") of iwlwifi (I haven't tested to make sure that these work, but hopefully they do). Untar, configure, make and make install them, and then run the "load" script and check "iwconfig". Let me know if you have any problems installing the new iwlwifi modules, and I'll give the new ones a try.

I think we should be able to get your wireless working again. I've found that sometimes the kernel modules get unloaded if I hit the wireless power switch off, and I have to load them manually again to get my wireless card recognized.

Hope this helps!
Mike

---

### Post by skier on 2008-01-24
Mike, thanks for the response!

```
comp@ME:~$ modprobe cfg80211 && modprobe mac80211 && modprobe iwl3945 && modprobe iwl4965 
```

FATAL: Error inserting cfg80211 (/lib/modules/2.6.22-14-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted


:confused:

---

### Post by mbsullivan on 2008-01-24
Hi skier,

Hmmm... try taking out cfg80211 and loading the others. The way it's written (which is my fault), it will quit as soon as it comes to an error, so you may be able to load the other three without incident. At the very least, I'd think that mac80211 should be no problem, since it's main-lined in the Gutsy kernel. If mac80211 and iwl4965 load, you may be good to go!

Anyway, assuming that mac80211 loads, then iwl3945 and iwl4965 should be no problem to get working ("no problem" meaning you don't have to recompile your kernel). Just download the [newest shapshot]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.23.tgz") of the drivers off of Intel's website, and compile and install them like normal.

I found that some versions of the drivers have compatibility issues with the x61. I don't have time right now, but if you have problems I'll see if I can get the latest release working for me. If not, I'll send you the version that I'm working off of directly (which we know should work).

So... in summation, see if you can get mac80211 loaded, and we'll work from there.
Mike

---

