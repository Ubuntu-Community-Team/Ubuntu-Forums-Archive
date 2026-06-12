---
title: "problems with NDISwrapper (Kubuntu 6.10)"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by AcedDesa on 2006-11-02
I have a Asus A6q000km laptop with AMD Turion64 and wireless:
00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I installed ndiswrapper on the fresh system:
```
sudo apt-get install ndiswrapper-utils-1.8
```

Then i installed windows driver for my wireless card:

```
sudo ndiswrapper -i bcmwl5.inf
```
```
sudo ndiswrapper -l
Installed drivers:
bcmwl5		  driver installed, hardware present
```

It seems installed properly :)

Then i trying this:

depmod -a
modprobe ndiswrapper

And no errors messages appears


Result of the "iwconfig" after installing driver

```
iwconfig
lo		no wireless extensions.

eth0	  no wireless extensions.

eth1	  IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
		  Mode:Managed  Access Point: Invalid
		  RTS thr:off   Fragment thr:off
		  Link Quality:0  Signal level:0  Noise level:0
		  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
		  Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0	  no wireless extensions.

```

"iwlist scan" returns "no scan results" like before ndiswrapper install.

Trying to do **ifup wlan0**:
```
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

What can i do next?

I'm sure i know "bcmwl5.inf" is the right driver, because it was copied from Mandriva's "/etc/ndiswrapper" which has been installed on my laptop before. Wireless works fine on my laptop with Mandriva.

Please tell me I'm wrong. Thanks :)

---

### Post by beemer on 2006-11-02
"Mode:Managed  Access Point: Invalid"

That's the key piece right there.  What I've found that to mean is there's a driver conflict.  Search around the forums for "blacklist broadcom".  

I believe your issue is that Kubuntu is loading a broadcom driver for your wireless (that's not working for you) and then you're loading ndiswrapper on top of it - so the two fight for the device and no one wins.

There are several threads on "blacklisting" the default broadcom driver and it's a easy fix (add one line to a blacklist file and reboot).

Beemer

---

### Post by juanx on 2006-11-02
check this post:

[http://xopen.dyndns.org/linux/z9200km/](http://xopen.dyndns.org/linux/z9200km/)

It got mine working ;-)

I agree with Beemer. The problem must be the bc43xx driver that comes with ubuntu messing around.

Hope that helps!

NOTE: Be sure you have the 64bits driver if you're using the amd64 ubuntu distro.

Good luck,

Juan

---

### Post by AcedDesa on 2006-11-02
Yeah, it works! :)

Added this row:
```
blacklist bcm43xx
```
in the /etc/modprobe.d/blacklist and reboot. It really helps.

Thanks a lot,friends :)

---

### Post by zeifertstc on 2007-04-12
Just noting something I noticed on your code copies. The interface was called eth1 and not wlan0. You were running "ifup wlan0" I wonder if you had tried running "ifup eth1" if perhaps that would have worked.

---

