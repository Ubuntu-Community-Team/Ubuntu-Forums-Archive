---
title: "Atheros AR2425 on Fujitsu Siemens"
date: 2010-02-03
forum: Hardware
---

### Post by jocaps on 2010-02-03
When I first installed Ubuntu 9.04 there was problem it detecting my wireless card. I upgraded to 9.10, still a problem.. then I researched a bit and I saw some nice instructions in the German ubuntu forum: [http://www.ubuntu-forum.de/artikel/45349/wlan-probleme-mit-atheros-ar5007eg.html](http://www.ubuntu-forum.de/artikel/45349/wlan-probleme-mit-atheros-ar5007eg.html)

following that I got my wireless running. But after a few restart of the laptop, I get a message on startup asking me some sort of password key ring (I can't remember).. I have no idea what that was (Im not sure if this is the WPA password, I typed the WPA password becaust it wouldnt work with my root password). After a reboot it didnt ask me this key ring thingy.. but instead refused to enable the wireless , i.e. wlan0 could not scan when I type 

```
sudo iwlist wlan0 scan
```

Here is what I did

```
jose@jose-laptop:~$ sudo ifconfig wlan0 up
jose@jose-laptop:~$ dmesg | grep ath
[    1.072449] device-mapper: multipath: version 1.1.0 loaded
[    1.072451] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.213653] ath5k 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.213665] ath5k 0000:04:00.0: setting latency timer to 64
[   21.213696] ath5k 0000:04:00.0: registered as 'phy0'
[   21.459216] ath: EEPROM regdomain: 0x60
[   21.459219] ath: EEPROM indicates we should expect a direct regpair map
[   21.459222] ath: Country alpha2 being used: 00
[   21.459223] ath: Regpair used: 0x60
[   21.472403] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
jose@jose-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
jose@jose-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```


Any ideas?

PS: Right now there are wireless SSID broadcast all around me.. so there should be something. I am using another laptop beside it that has connection to an unhidden SSID.

---

### Post by elpadre on 2010-03-15
Hello there, 
I have the same problem and I don't have the solution for the moment.
I just installed Ubuntu yesterday and since then I am trying to turn the WIFI on. 
At first it was off, then I installed a airsomething program (Can't remember the name, I have read so much things already but obviously not enough ....) , then I tried with windows driver ... finally I did it ( I think this package with Atheros drivers did it)! 
WiFi is on now but same problem persist as yours. It just can't detect networks.

If you found any solution , or if there is anyone who can help it will be very nice.
I have read a lot of things how to turn it on , but about the scanning problem I never found something. I downloaded 2 books for Ubuntu but nothing different was written there for my problem.

Thanks for your time. I am sorry that I am asking such a ridicules questions(for you) but since 1993 I am working with MS stuff so it is a but difficult for me now.
One more time thanks. :)
:D

---

