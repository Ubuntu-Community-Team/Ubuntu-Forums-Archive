---
title: "ipw2200 on Breezy"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by Alf Stockton on 2006-02-26
If I 
iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:C9:0D:2B
                    ESSID:"Stockton"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=97/100  Signal level=-28 dBm
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    Extra: Last beacon: 575ms ago

however if I
 
sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:6e:2c:50
Sending on   LPF/eth1/00:12:f0:6e:2c:50
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Please tell me what I have forgotten to do.

---

### Post by cbudden on 2006-02-26
You could try sudo /etc/init.d/networking restart

---

### Post by Alf Stockton on 2006-02-26
Tried that and it made no difference.:(

---

### Post by ape on 2006-02-26
Upgrade to the latest ieee80211 and ipw2200 drivers from the following locations:

[http://ieee80211.sf.net](http://ieee80211.sf.net) (currently 1.1.12)

[http://ipw2200.sf.net](http://ipw2200.sf.net)  (currently 1.1.0)

They've made HUGE leaps in stability since the version that ships with Breezy.

---

### Post by Vorian on 2006-02-26
encryption problem....

turn encryption off on your box, restart breezy.

then reconfigure

---

### Post by Alf Stockton on 2006-02-28
I have installed the latest software without any more success.
When I:-
sudo wpa_supplicant -w -i eth1 -D wext -c /etc/wpa_supplicant.conf
I get:-
which gives me:-
ioctl[SIOCSIWPMKSA]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WPA: No assoc_wpa_ie set - cannot generate msg 2/4
WPA: Could not verify EAPOL-Key MIC - dropping packet
Trying to associate with 00:14:bf:c9:0d:2b (SSID='Stockton' freq=0 MHz)
WEXT auth param 6 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
ioctl[SIOCSIWGENIE]: Operation not supported
WEXT auth param 0 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 1 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 2 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 3 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 8 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
Association request to the driver failed

---

### Post by sdb2028 on 2006-02-28
I am also having problems with my wireless connection. I have seen several threads and replies where "MANY" other people have the same problem. As far as updating the drivers, can anyone give better instructions as to how to acomplish that than what the INSTALL file say's?
I have found the a lot of the syntax does not work, it is pretty criptic.
We, (or I) need someone to translate it into usable terms.
Please help,
Thanks,
Steve

---

### Post by Vorian on 2006-03-01
[QUOTE=Alf Stockton]If I 
iwlist eth1 scan.......
                    **Encryption key:on**

Please tell me what I have forgotten to do.[/QUOTE]

turn your encryption off.
reboot your system.
run dhclient
set your encryption
run iwconfig eth1 key s:(passphrase)
reboot again

you will be able to use the wifi gui from this point forward.

i use this same driver for my wifi.  i did all this legwork with the hoary hedgehog release.

---

### Post by dotslashroot on 2006-03-02
[QUOTE=Vorian]turn your encryption off.
reboot your system.
run dhclient
set your encryption
run iwconfig eth1 key s:(passphrase)
reboot again

you will be able to use the wifi gui from this point forward.

i use this same driver for my wifi.  i did all this legwork with the hoary hedgehog release.[/QUOTE]

I am having the same problem.  What file do you edit to turn the encryption off?  Thank you.

Lucas

---

### Post by Vorian on 2006-03-02
You have to configure encryption on your router, not your OS.  You need to use your browser and put in the address (like [http://192.168.0.1](http://192.168.0.1)) You may need to use your CAT5 if you cant get to it via your wireless (like when you set it up)

Good Luck!

---

### Post by dotslashroot on 2006-03-02
[QUOTE=Vorian]You have to configure encryption on your router, not your OS.  You need to use your browser and put in the address (like [http://192.168.0.1](http://192.168.0.1)) You may need to use your CAT5 if you cant get to it via your wireless (like when you set it up)

Good Luck![/QUOTE]

Thanks for the fast reply.  I already turned it off on the router because I could not get an IP from the DHCP server.  I initially put a key in the card config.  What file is that stored in?  Like the example above where it says encrytption key: on?  What file can I edit to set that to = off?  Thanks!

---

### Post by Vorian on 2006-03-02
[QUOTE=dotslashroot]Thanks for the fast reply.  I already turned it off on the router because I could not get an IP from the DHCP server.  I initially put a key in the card config.  What file is that stored in?  Like the example above where it says encrytption key: on?  What file can I edit to set that to = off?  Thanks![/QUOTE]

Router encryption is router specific. Your wifi card "wants" to get in as far as possible.  

What do you see when you [iwlist eth1 scan]? can you post your scan results?

---

### Post by dotslashroot on 2006-03-05
[QUOTE=Vorian]Router encryption is router specific. Your wifi card "wants" to get in as far as possible.  

What do you see when you [iwlist eth1 scan]? can you post your scan results?[/QUOTE]

This is what I get:

eth1 no scan results


It is listed in networking and it says it is active.  Any ideas?  Thank you!

---

