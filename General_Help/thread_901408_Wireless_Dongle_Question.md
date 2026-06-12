---
title: "Wireless Dongle Question"
date: 2008-08-26
forum: General Help
---

### Post by Stavro on 2008-08-26
Hi, I just have a general question please. I have the latest Xubuntu 8.04 live CD and I tried it out the other day. Everything seems to work well, seemingly even my wireless USB dongle works too. It is the BlueNext BN-WD54G and as far as I'm aware it works out the box on the latest versions of the OS. My question is though, whilst it seems to be happy flashing away, is it common for wireless networks not to appear in LiveCD mode? I was hoping to try out the internet capabilities with the LiveCD, but I have a blank network list in the wireless control panel. I know the router broadcasts SSID information.

---

### Post by Sycron on 2008-08-26
type in a terminal:
```
sudo iwlist scan
```
and paste the output :)

---

### Post by Stavro on 2008-08-26
Thanks, here is the output:
```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2A:6D:0F:AD
                    ESSID:"philips"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/100  Signal level=-76 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000004f7c0d49a
```

---

### Post by Stavro on 2008-08-26
Any ideas why I can't see my wireless home network in the network manager and yet the sudo code above seems to recognise it?

---

### Post by Stavro on 2008-08-26
Any help would be appreciated please. Maybe Wireless just doesn't work in LiveCD mode?

---

### Post by Rome.konig on 2008-08-26
i use to have that same problem. i'm dont know the cause of the problem, have you tried using different type of encryption? like using wep key instead of wpa? or vice versa. they way i have mine set up is, i broadcast a ssid but keep it hidden or ghost, with no password. i make the name extra weird just in case. and all i do is type in the name in search field to access it.

---

### Post by Sycron on 2008-08-28
I dislike a bit the default netowrk manager... I would try something else, try wicd.

---

