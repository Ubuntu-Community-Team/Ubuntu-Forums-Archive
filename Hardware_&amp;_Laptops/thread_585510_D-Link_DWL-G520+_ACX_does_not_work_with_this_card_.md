---
title: "D-Link DWL-G520+: ACX does not work with this card (no WPA), use nsidwrapper."
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by MadeR on 2007-10-21
For anyone having problems with this card:
 
blacklist acx module and use only ndiswrapper.
I do not know the reason why, but acx drivers supports only those silly, easily crackable WEP protection scheme.

---

### Post by wcgoh on 2007-10-31
Which driver did you use for the Ndiswrapper? I used the one that came along in the CD, but it didn't work.

---

### Post by MadeR on 2007-11-01
> **wcgoh said:**
> Which driver did you use for the Ndiswrapper? I used the one that came along in the CD, but it didn't work.
inf file
sys file 
and firmware


did you use them all?

---

### Post by MadeR on 2007-11-01
I created an archive with the files:

[http://www.massimilianodellarovere.eu/linux/gplus.zip](http://www.massimilianodellarovere.eu/linux/gplus.zip)

remember to blacklist acx module and issue a ```
sudo ndiswrapper -m
```

---

### Post by wcgoh on 2007-11-01
Cool. Thank  you.

Going to try it later.

---

### Post by wcgoh on 2007-11-01
Oh My wireless network finally worked. Thanks to your driver file. Now i have                                      to find how to fix the kvm switch.

---

### Post by MadeR on 2007-11-02
> **wcgoh said:**
> Oh My wireless network finally worked. Thanks to your driver file. Now i have                                      to find how to fix the kvm switch.

what's wrong with kvm?

---

### Post by kboykowboy on 2007-11-02
I'm just curius here (cant spell that) - IF the network card it self by default does NOT support WPA (like mine syair b-100) CAN you make it work on a WPA network anyway?! by using Ndiswrapper e.g.?!

---

### Post by MadeR on 2007-11-02
> **kboykowboy said:**
> I'm just curius here (cant spell that) - IF the network card it self by default does NOT support WPA (like mine syair b-100) CAN you make it work on a WPA network anyway?! by using Ndiswrapper e.g.?!
I think so, but
1) the firmware should be made for your card
2) the card should be as simple as possible and everyting should be sw oriented

---

### Post by kboykowboy on 2007-11-02
hmm.. nice... i have spendt a couple of evenings on it but never tryed Ndiswrapper.. so i also need wpasupplicant?!

---

### Post by MadeR on 2007-11-02
> **kboykowboy said:**
> hmm.. nice... i have spendt a couple of evenings on it but never tryed Ndiswrapper.. so i also need wpasupplicant?!

yes you have to use wpa_supplicant and create a configuration file in /etc/wpa_supplicant/ or you can use the (k)networkmanager.

so:
add *acx* to **/etc/modprobe.d/blacklist**

decompress the archive and in that folder run *sudo ndiswrapper -i gplus.inf*, then *sudo ndiswrapper -m*

*sudo depmod -a*
*sudo modprobe -r acx*
*sudo modprobe ndiswrapper*

restart the (k)networkmanager


if you want to use wpa_supplicant
man 5 wpa_supplicant

for a fast and dirty try (WPA, pre shared key, TKIP):

add the following lines to **/etc/wpa_supplicant/wpa_supplicant.conf**
          network={
               ssid="[color=red]your network name[/color]"
               scan_ssid=1
               key_mgmt=WPA-PSK
               psk="[color=red]network password[/color]"
          }


then *sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf   -D [color=red]****[/color] -i [color=red]interface name (for example wlan0)[/color] *

substitute **** with either wext or ndiswrapper.
for complete list: wpa_supplicant -h

---

