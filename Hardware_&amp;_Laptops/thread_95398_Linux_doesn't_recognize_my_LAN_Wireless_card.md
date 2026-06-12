---
title: "Linux doesn't recognize my LAN Wireless card"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by GabrielWolff on 2005-11-26
Hey all.
I finally decided to move to linux today, and so I did. Even though I expected some problems I didn't expect my wireless card to not function. It seems that I'm  missing the correct Linux supported driver, or I don't know what..

1) details of the card are: EW-7108PCg  	
Edimax
802.11g/b Wireless LAN 32-bit Cardbus

 2)I didn't find any Linux support in the Edimax website, nor did I find any drivers suitable to my wireless card that can be installed on Linux.
3)I tried opening the console ( terminal) and typing :
iwconfig
-or-
sudo iwconfig
which resulted in the system replying:

lo                no wireless extensions
ethO           no wireless extensions 
sit0               no wireless extensions
raO            RT2500 wireless ESSID:""
Mode:Managed  Frequency= 2.412 GHz        Bit rate: 1 Mb/s
RTS thr: off           Fragement thr:off
Encryption key:off
Link quality=0/100   Signal level=-120 dBm   Noise level:- 256 dBm
Rx invalid nwid:0    Rx invalid crypt:0    Rx invalid frag:0
Tx excessive retries:0    Invalid misc:0    Missed beacon:0


Thanks for your replies..
Eli

---

### Post by mips on 2005-11-26
Your card should work out of the box.
Try:
```
System>>Administration>>Networking Select device ra0>>properties tick configure, enter WEP and IP settings, OK, then activate.
```

---

### Post by GabrielWolff on 2005-11-27
Hey, thanx for the reply.

Could you, tough, give me idiot-proof answers as for what I should type in for
1) WEP
2) IP settings.

I don't even know what a WEP is...

Thanx again

Eli

P.S.: I love Ubuntu, especially the console. Weird for beginners, I know. but hey! It's really much faster than endless GUI-packed programs under Windows.

---

### Post by mips on 2005-11-27
[QUOTE=GabrielWolff]
Could you, tough, give me idiot-proof answers as for what I should type in for
1) WEP
2) IP settings.

I don't even know what a WEP is...
[/QUOTE]

WEP=Wired Equivalent Privacy and it is basically a method to secure your data across the air. Not very secure though, rather use WPA.

Your 3 options are: Open(No encryption), WEP(Average encryption) & WPA(Strongest encryption)

Where does your wireless card connect to ? Your personal AP, a public AP or a private AP. AP=Access Point

The IP address is either assigned dynamically via DHCP or configured statically. The Encryption method gets determined by whoever owns the AP and they assigng the encryption string.

If you are trying to connect to your own personal AP I suggest you go for Open by disabling all encryption and configuring a static IP address. Once you have this working then you can try out assigning an IP via DHCP. Once this is done you can start enabling WPA or WEP.

I'm not that clued up on Linux wireless configs. I suggest you search the Networking forum and also look out for posts by Lambert.

Sorry I cannot be of any more help.

---

