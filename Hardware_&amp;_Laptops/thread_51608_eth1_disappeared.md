---
title: "eth1 disappeared"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by Stealth on 2005-07-24
I have no idea why either. I had just installed my WPA and IPW2200 drivers on Friday fine. Yesterday everything was working cool, I downloaded ubuntu-desktop and xfce (I have Kubuntu) and it was working fine yesterday too. Today I turn on my laptop to find that wpasupplicant is being disabled. Why? Because there is no network interface to use. I type iwconfig to see that eth1 is gone. It had to be the update yesterday, but what the heck would disable my wireless card?? How do I get it bacK?

---

### Post by Stealth on 2005-07-31
I guess no one's had recent upgrade problems with their wireless networks?  :???:

---

### Post by ketilkn on 2005-08-01
Just an idea. Maybe you have some sort of hardware switch that turns of the Wifi-chip. I have got one on my P7010. My switch will not completly disable my card but just prevent a signal from being transmitted. Your laptop could be different.

---

### Post by Stealth on 2005-08-01
To disable my card I press Fn+F2. Unforuntaely Ubuntu never really supported that key combo so it was on all the time. Even if I wasn't connected though, I had the eth1 interface. Now its not even there!

---

### Post by plasmatonic on 2005-08-01
[QUOTE=Stealth]I have no idea why either. I had just installed my WPA and IPW2200 drivers on Friday fine. Yesterday everything was working cool, I downloaded ubuntu-desktop and xfce (I have Kubuntu) and it was working fine yesterday too. Today I turn on my laptop to find that wpasupplicant is being disabled. Why? Because there is no network interface to use. I type iwconfig to see that eth1 is gone. It had to be the update yesterday, but what the heck would disable my wireless card?? How do I get it bacK?[/QUOTE]
 I had similar problems on my Thinkpad T40p. The key combonations are bios controlled so the OS won't prevent the FN-F5 (in my case) or FN+F2 in yours from functioning... there may be no onscreen display but the hardware will be turned on/off regardless. 

At any rate, my problem was that I had to manually turn it on every boot. I updated hotplug and voila it was working fine again.

---

### Post by luca_linux on 2005-08-01
Have you tried to get it back through the network panel or iwconfig/ifconfig?

Could you post your "dmesg | grep ipw"?

---

### Post by Stealth on 2005-08-02
it says:
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

I'm not really sure how I would get it back. I type iwconfig and only get lo and eth0. KControl shows that I only have eth0 as a network interface...:(

---

### Post by luca_linux on 2005-08-02
There's a problem with the driver due to the presence of old modules...
Try to install ipw2200 and ieee80211 again, following this HowTo: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by Stealth on 2005-08-02
awesome, thx luca! :D

I'm not sure why that happens though. I followed your guide, everything worked fine, after an update of a bunch of stuff it stopped working...I wonder what went on during the update. Ok, cool...got my wireless back on the laptop! ^_^

---

### Post by dan4444 on 2006-06-13
I have a similar problem on my laptop (I have an Intel Proset Wireless card). In my case though, eth1 (my ethernet connect) became eth0.

In any case though, the results of "dmesg | grep ipw" on my system are:

[4294683.454000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, git-1.0.8
[4294683.454000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294683.631000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection[4294683.641000] ipw2200: ipw-2.4-boot.fw load failed: Reason -2
[4294683.641000] ipw2200: Unable to load firmware: -2
[4294683.641000] ipw2200: failed to register network device
[4294683.641000] ipw2200: probe of 0000:06:03.0 failed with error -5

Does this mean that I need to re-install the firmware for my wireless card, or something else? Anyone have an idea on this?

---

### Post by jome on 2007-01-21
I have the same error messages:

dmesg | grep ipw
[4294685.312000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294685.312000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294685.312000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294695.312000] ipw2200: ipw-2.3-boot.fw load failed: Reason -2
[4294695.312000] ipw2200: Unable to load firmware: 0xFFFFFFFE
[4294695.312000] ipw2200: failed to register network device
[4294695.312000] ipw2200: probe of 0000:06:0a.0 failed with error -5

My wireless was working fine (including wpa-supplicant) under the name eth0. But after I used the wired connection, that became eth0. Now I can not get the wireless to work under either eth0 or eth1.

---

### Post by jome on 2007-03-26
[http://www.openthought.org/blosxom.cgi/2006/02/13](http://www.openthought.org/blosxom.cgi/2006/02/13)

---

### Post by jome on 2007-03-26
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=349937](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=349937)

still it doesn't work

---

