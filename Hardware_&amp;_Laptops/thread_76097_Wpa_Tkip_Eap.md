---
title: "Wpa Tkip Eap"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by Trinitrogen Oxide on 2005-10-14
Im trying to get my Ubuntu laptop (HP Pavilion DV1000)  working on Purdue's wireless network, called PAL 2.0. Like I said in the title, it used WPA with TKIP encryption, with... nevermind it'd be better to just link you

[http://www.itap.purdue.edu/airlink/setup/winxp.cfm](http://www.itap.purdue.edu/airlink/setup/winxp.cfm)

I've found the WPA + ipw2200 guide, but Im not totally sure it can apply to my situation wpa_supplicant.conf file he suggests

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```

Do I even use wpa_supplicant for this? Or do I use xsupplicant.

But I don't think that will work for me. First correct me if Im wrong but should it be key_mgmt=WPA for me? How to I set TKIP as my encryption, and PEAP as my authentication? And how do I set the CA to Thatwte Premium Server CA for the PEAP. Finally at the end it says "PSK" for my secret key, but I don't really have a secret key. I just have my Purdue username/password?

I'd like it so I have two seperate profiles, one for when Im in my house on my open wireless, and one for when Im on campus using this PAL network

so many questions, I know and im sorry. any help is appreciated.

---

### Post by Trinitrogen Oxide on 2005-10-14
ugh, sorry I thought i was posting in the networking section... :(

---

### Post by mutejute on 2005-10-16
hi trinitrogen. im just wondering if you managed to configure WPA in your ubuntu breezy using wpa_supplicant. were u successful?

---

