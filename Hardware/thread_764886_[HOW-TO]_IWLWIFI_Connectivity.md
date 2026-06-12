---
title: "[HOW-TO] IWLWIFI Connectivity"
date: 2008-04-24
forum: Hardware
---

### Post by Daelyn on 2008-04-24
Hi.

As many of you might know and have faced, there is a bit of issues connecting to wireless networks with the IWLWIFI driver. The driver/card seems to work fine, but it just won't associate and connect to any access points. 

Now, because the iwlwifi driver comes as standard in Hardy, I guess we'll have a lot of members having issues with this.

After a few hours of search and find the other month, I came across a solution unknown to most of us. 

Copy of 
**/etc/network/interfaces**

```
iface wlan0 inet dhcp
pre-up ip link set up dev wlan0 # (Needed with iwlwifi)
wpa-driver wext
wpa-ap-scan 1
wpa-key-mgmt WPA-PSK
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-ssid xxxxxxxxxxxx
wpa-psk xxxxxxxxxxxxxxxxx
auto wlan0
```

Here I'm using a WPA/WPA2 encrypted connection. Note that is neither or, it is both at once. Probably nothing common in most households though.

What is the *solution *and *what is different *you might ask?
```
 pre-up ip link set up dev wlan0 
```
That is the _key to our connectivity _with iwlwifi it seems.

So, what do you do to implement this?
Well, every time you use the network manager to search and connect, this line will vanish from your interfaces config file. So, using network manager is out of the question.

**MANUAL configuration is needed??**.

Use the line I supplied (replace the interface name if needed) and set up a manual configuration for the connection to your wireless network.

Have a look at the following thread for information on connectivity to WEP/WPA/WPA2/LEAP/PEAP/ASE etc. 
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

I hope this is of use to all of us Intel nerds.

---

### Post by oodlesOfmoodles on 2008-04-24
How do I install ipw drivers and uninstall iwl drivers?

My shool uses OPEN algorithm dynamic WEP MSCHAPV2 and iwl doesn't support that configuration with wpa_supplicant which is the only way i can get it to work.

This is quite critical if I want to bring Ubuntu to my school.

Thanks!

---

### Post by Daelyn on 2008-04-25
> **oodlesOfmoodles said:**
> How do I install ipw drivers and uninstall iwl drivers?

My shool uses OPEN algorithm dynamic WEP MSCHAPV2 and iwl doesn't support that configuration with wpa_supplicant which is the only way i can get it to work.

This is quite critical if I want to bring Ubuntu to my school.

Thanks!

I don't know how to install the ipw-driver on hardy.
Should be some threads about it here and there though. You are most likley not the only one who have asked.

I'm gonna look into it tonight.

---

### Post by oodlesOfmoodles on 2008-04-25
Thanks for your help!

---

### Post by GeoMX on 2008-05-01
Thanks a lot! I've managed to connect to my wireless network thanks to your advice :).

Just one question, is it possible to see nearbye wireless networks in network-admin? When using Gutsy, I would highlight the wireless connection and click on Properties, and on the ESSID there would be a list of available networks and a percentage/quality of their signal, but now I can't see anything :confused:.

---

### Post by GeoMX on 2008-05-07
Updating info...

The use of these drivers is really painful. Everytime I turn on my lap, I would have to enable/disable/scan in order to connect to a wireless network, sometimes it works just after some tries, sometimes after a lot of them.

I have two questions:
how can I make the iwlwifi drivers work better?
how can I go back to my previous drivers?

I'm using a Dell XPSM1330 with an Intell 3945 wirelss card.

Thanks in advance for your help :).

---

### Post by Daelyn on 2008-05-17
Hi.

To be honest, I have no idea why the network-admin doesn't scan properly. it sometimes do, but, I think it only does when it in pre-up state and ain't associated.

Scan with iwlist works fine, if I'm not associated. Just scan for the network you want and edit it into /etc/network/interfaces.

It is a tricky driver, but, to be fair, the stability of it is alot greater than the ipw drivers. I like the iwlwifi but it definately needs more attention than it gets now.

---

