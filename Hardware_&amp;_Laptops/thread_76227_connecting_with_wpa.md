---
title: "connecting with wpa"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by bb002 on 2005-10-14
It took awhile but I finally got wpa working. it appears that the "ipw" driver that comes with ubuntu 5.04 doesn't support wpa. however the current version does. so i manually compiled and updated the "ipw" driver since it wasn't listed in synaptics and if it was i missed it. I followed [this]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=howto+wpa") howto by luca_linux. other than that i have done nothing outside of synaptics.

Now I can connect with WPA and works perfect....almost. Home still has a few issues but i can eventually connect. maybe someone has a pointer or two to help me.

/etc/wpa_supplicant.conf

```


ctrl_interface=/var/run/wpa_supplicant

#ap_scan=2

network={
       ssid="fakehomessid"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       psk="supersecurepass"
}


network={
       ssid="ssidatwork"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       psk="superinsecurepass"
}


```


As I said work connects without a hitch. Home however requires a bit of trickery. Home has a hidden ssid but making scan_ssid=1 doesn't work. inorder to make it connect i have to uncomment the ap_scan=2 then run wpa_supplicant, use wpa_cli to terminate wpa_supplicant, comment ap_scan=2 out again then run wpa_supplicant one more time. Now i can connect at home.

What I want to know is why must I do this to connect at home!? if i enable ssid broadcast it works fine, no trickery, no nothing. It just connects like work. disable ssid broadcast and i have to go through all of that again.

PS:
 I read in another post that you should click on something by someone's avatar when they do nice things to boost their rep. what is it i'm supposed to be messing with those coffee cups? The only thing I found to be clickable was the avatar itself and that take me to the member's page.

---

