---
title: "Wireless configuration"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by repeat on 2006-04-08
My broadcom wireless adapter (4306) was detected in the installation process of Ubuntu Dapper Drake.

The output of 'iwconfig' is:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off

sit0      no wireless extensions.

Does this mean a working driver for the card are loaded? If yes, how do I configure it to Work?

Or must I use Ndiswrapper?

---

### Post by repeat on 2006-04-08
I am now trying ndiswrapper, following these guidelines: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Everything went well until the [FONT="Courier New"]'dmesg'[/FONT] command which gave me the following error:

```
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed .
```

Anyone who knows what this means? Or how to fix it?

---

### Post by rosslaird on 2006-04-09
I'm getting exactly the same error message.

-- bump ..

---

### Post by altor on 2006-04-09
First  download and install your firmware. look at:
[http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/)

Look to the way to install ndiswrapper and to use it. 

Try lsmod and if you see amodule like bcm43xx:
 $ rmod bcm43xx (do not use toghether ndiswrapper and bcm43xx)

Then:
modprobe ndiswrapper
ndiswrapper -m
eth0 down
eh1 down
eth0 up
iwconfig 
[now you should see your wireless device as wlan0]

finally
iwconfig wlan0 essid <name-access-point> key <yor-wirelwss-wepkey>

In this way I was able to get my device work just a few days ago.

Bye!

---

### Post by repeat on 2006-04-09
Hi, and thanks for your reply. It really helped me alot!

My wireless adapter connected to my neighbours unsecured wireless network ;)
Well, next step is to get my adapter to connect to my own wireless router.

I seems like it connects, but i can't get an IP adress.
And it detects several wireless networks in my area...

[IMG]http://home.broadpark.no/~rhov/linux/kwifi.png[/IMG]

This is the output of 'iwconfig':

```
eth0      IEEE 802.11b/g  ESSID:"popkorn"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:90:4B:8A:46:7B
          Bit Rate=11 Mb/s   Tx-Power=13 dBm
          RTS thr:off   Fragment thr:off

```

As you see, my adapter still is 'eth0'. Not wlan0. Is it something wrong?

How can I set set the 'index key' (1-4) and Security mode to Shared key?

I also tried the command 'dhclient eth0':

```
sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:13:d4:30:ab:81
Sending on   LPF/eth0/00:13:d4:30:ab:81
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.1.116
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

--- 192.168.1.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

Why 255.255.255.255? The subnet mask on my router in 255.255.255.0 :-k

---

### Post by altor on 2006-04-09
To me the point is that iwconfig shows now both "popkorn" and "Nickname Broadcom...".

My guess is that both modules nidiswrapper an bcm43xx are still there.
[I assume that you gave the correct wep Key].

First of all I'd try: 
rmmod both ndiswrapper and bcm43xx, then 
modprobe ndiswrapper again.
ndiswrapper -m again  [this command writes an alias for wlan0 - see man ndiswrapper]
Be sure that eth1 is down and that no network cable is plugged.

Try to blacklist bcm43xx as well, otherwise it will come up at boot (I don't remember exactly which file is involved but it is quite easy to find it, I guess). Then reboot.

Broadcasting on 255.255.255.255 for dhclient is nice, but  your signal is weak so it could be difficult to get an ip. [my signal strength is now 99].
So try to get a static ip with gnome network tool. As a matter of fact I think that now you just need an ip. :) :)

Good Luck

Bye!

---

### Post by repeat on 2006-04-10
Hi.

And thanks again :)
It's all working now. The signal is excellent.
My adapter is still eth0, not wlan0 :-k 

Is it possible to use the kernel loaded bcm43xx driver?(without ndiswrapper?)

---

### Post by altor on 2006-04-10
I am so happy I could help you!

:) :) :)

If your device does work, I should not care about eth0/wlano!

I have not tryed with bcm43xx driver, I am afraid to get in trouble...
If you succeed let me know.


Ciao!

---

### Post by altor on 2006-04-11
By the way...

I would appreciate to know how did you get your ip adress and improve the signal quality.

Bye.

---

### Post by teeler on 2006-04-14
Repeat:

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-e70dd6b5c57894d32e3eddc4f3e21d7d6d02230f](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-e70dd6b5c57894d32e3eddc4f3e21d7d6d02230f)

enjoy!

---

