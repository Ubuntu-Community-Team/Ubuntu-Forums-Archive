---
title: "Demand for ipw22 + wpa + wlan roaming?"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by Tomcat_ on 2005-06-15
After using [this HOWTO](http://ubuntuforums.org/showthread.php?t=26623) I did have wpa with the ipw2200 drivers (Centrino wlan); However, there were still some bugs (no wlan roaming, crashing drivers).

If there is demand I could write a HowTo on how to get ipw2200 working with wlan roaming (plain, WEP and WPA) being quite stable. Anyone want it?

---

### Post by skela on 2005-06-15
I have an HP dv1170ea laptop with a 2200 b and g wireless ipw and I could certainly use some help getting different aspects of wlan working.

I did follow the how to , got everything working and everything... Eth0 was a wired inet connection, Eth1 wireless... But after a simple reboot that all changed and I can only locate the Eth0 device, thus confining me to the wire ... I don't understand how my wireless device could just disappear... Any help is much appreciated...

---

### Post by luca_linux on 2005-06-16
Try to type:
```
dmesg | grep ipw
```
And post the result.

---

### Post by luca_linux on 2005-06-16
[QUOTE=Tomcat_]After using [this HOWTO](http://ubuntuforums.org/showthread.php?t=26623) I did have wpa with the ipw2200 drivers (Centrino wlan); However, there were still some bugs (no wlan roaming, crashing drivers).

If there is demand I could write a HowTo on how to get ipw2200 working with wlan roaming (plain, WEP and WPA) being quite stable. Anyone want it?[/QUOTE]
 Yes, why not.
Then we could also merge the two howto.

---

### Post by skela on 2005-06-16
skela@davinci2:~$ dmesg | grep ipw
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_freq_to_channel
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_get_geo
ipw2200: Unknown symbol ieee80211_is_valid_channel
skela@davinci2:~$
______
What? Heh...

---

### Post by luca_linux on 2005-06-16
Ok, it sounds like you didn't remove all the old modules before installing the newer ones.
Follow again the howto and make sure you remove all ieee802*.ko and ipw2200.ko modules. Then copy the newer into the other directory as said in the howto.

---

### Post by skela on 2005-06-16
Hey thx, now it's working :D

One problem though, my home network has a wep key... if I use the network gui thing and configure eth1 (wireless) and look at the properties with the wireless connection I can only get it working if I write the key in there, and press ok... it all works as long as I dont close the window for network settings.

Heh if you have any problems understanding , I'd be glad to explain, I am a ubuntu newb afterall...

So the problem: When I return to the properties of my wireless connection and look at the key the number of *** does not match with the key I wrote earlier... That means that the network settings manager changes the key when I "ok" it :p
But why should that matter? I believe the key I write in is Hex , and the things stores it as ascii... why?!

---

