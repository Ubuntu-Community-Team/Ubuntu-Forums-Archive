---
title: "ubuntu wifi problem WEP"
date: 2008-04-28
forum: Hardware
---

### Post by jonniie on 2008-04-28
so i have just installed ubuntu 8.04 on my Thinkpad X61 and i am having some trouble with the wifi.

I can connect to any network that is unprotected but when it comes to using WEP it just doesn't want to work.

does anyone have any ideas?

---

### Post by Yellow Pasque on 2008-04-28
Try to connect to a WEP network. Input the key when/if prompted, then see what the iwconfig command says about the connection.

If you're not prompted for a key, use the iwconfig key command to enter it. For example:
```
sudo iwconfig wlan0 key ABC1234
```

---

### Post by Jose Catre-Vandis on 2008-04-28
what lines do you have in your /etc/network/interfaces file? Your network adapter appears to work so it must simply be a matter of adding a line for the key?

I am using WEP and have the following lines in my interfaces file:
```
auto wlan1
iface wlan1 inet dhcp
wireless-essid myessid
wireless_mode managed
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
```

you will need to get the key from your router, 13 character for 64 bit, and 26 character for 128 bit encryption. Your interface may well be different from wlan1 (could be eth0, wlan0, etc etc). if you have a static IP, you will need to add the lines for that.

---

### Post by cre8ivgil on 2008-04-28
I am having the same issues, I could connect to unprotected networks but as soon as I turn on WEP in my router I would no longer connect. I verify the key over and over again so I know I am entering the correct key, and I've also verify that it is listed in etc/network/interfaces. I have been trying to figure this out since yesterday with no luck. My kids laptop one running Vista and the other running XP connect using the WEP key with no problem. Once again if I turn off WEP I connect instantly, turn it back on and no connection. I am starting to sweat!

---

### Post by cre8ivgil on 2008-04-28
Got mine working with Wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) I was running in about five minutes after installing this wonderful network utility. In preferences I kept the WPA Supplicant Driver at the default setting after installation (wext) and set the WEP (Hex) encryption. Launch Firefox and Bingo!

---

### Post by jonniie on 2008-04-28
```

auto lo
iface lo inet loopback

```

that is all that is in my /etc/network/interfaces file

i tried wicd and still no joy.

---

### Post by Jose Catre-Vandis on 2008-04-29
I have network manager turned off in "Sessions" and also had to kill wpa-supplicant to get WEP connection up and running (this is because at work I connect to WPA-PSK wireless and at home to WEP)

---

### Post by subzero316 on 2008-04-29
Try with **WICD **

---

### Post by jonniie on 2008-04-29
no luck, i am new to all this so i don't really have any ideas!

---

### Post by Jose Catre-Vandis on 2008-04-29
have you tried editing your interfaces file to look like the one I posted above, and killed wpa_supplicant?

---

### Post by jonniie on 2008-04-29
ok.  i now have wifi working with my AP but originally i was trying to get it working with my iMac and internet sharing. never mind eh?

---

### Post by Jose Catre-Vandis on 2008-04-29
Now you tell us ;)

Glad it's all sorted, anyhow.

---

### Post by jonniie on 2008-04-30
is there any reason why the WEP would work with an access point but not with the iMac?

---

