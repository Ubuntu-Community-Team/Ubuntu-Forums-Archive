---
title: "How do I get a Shared WEP key to work"
date: 2005-11-11
forum: General Help
---

### Post by ThomThom on 2005-11-11
Hi.
I've just installed Ubuntu 5.10 and are trying to connect it to the network/internet.

The wireless network uses a shared WEP key. I have not been able to configure Ubuntu to connect when it's enabled. I did a test where I set the router to ont use a WEP and had the network "open". Then Ubuntu connected automaticly without any problem. (DCHP)

Once a shared WEP key (ASCII) is set for the network Ubuntu fails to connect. I've searched the forum for similar posts, but I could not make much sence out of them. (Note, I am completely new to Linux. I've allways been a Windows user I just installed Ubuntu in a dualboot.)

How can I set up my Ubuntu installation to connect to a wireless network that's using a shared WEP (ASCII) key?

-cheers!

---

### Post by ThomThom on 2005-11-12
Hm. I also tried to setting the Authentication from Shared to Open, just to see if that worked. But with no luck. Then I went back to disabling the key just to see again. But this time it didn't work. I couldn't get connected, even though I did once before. I even had reverted to the origianl /etc/network/interfaces file.

---

### Post by Lambert on 2005-11-12
What kind of card are you using? If you can post the output of

```
sudo lshw -C network
```

please do.

I'm using a dwl-g650 card with atheros chipset. wep worked immediately for me with no other configuring. I'm using wep; open; hexadecimal

---

### Post by emperor on 2005-11-12
[quote=ThomThom]

How can I set up my Ubuntu installation to connect to a wireless network that's using a shared WEP (ASCII) key?

-cheers![/quote] 
The "System/Admin/Networking" configuration setup is missing the an entry for the "channel". However, the configuration file that is created can be editied manually, as it is just a text file:

sudo gedit /etc/network/interfaces

My wireless section in the "interfaces" file looks like this:

iface eth1 inet static
address 192.168.10.103
netmask 255.255.255.0
gateway 192.168.10.1
wireless-essid FlyingPenguin
wireless-key Cef81bff9A
wireless-channel 4
wireless-mode managed
wireless-ap 00:0C:FD:8F:F8:AE

Yours should have all but the "wireless-ap" entry and the "wireless-channel". I use a fixed IP at home, which is also listed above. Also, a HEX Wep key is specified. You should specify an open WEP key, which is actually more secure than the "restricted" type. Some wireless cards/drivers require some extra commands to use a "restricted" WEP key; the dwl-g650 was one of the cards with this problem. My daughters old Dell i3200 has a dwl-g650 and gave me quite a problem. 

If you have a laptop, you may want to install "wifi radar". This will let you create several different settlings for a variety of AP's.

---

### Post by ThomThom on 2005-11-12
The router is a Skyr@cer Pro WBR 654.

The Authentication options for it is:
* Open System (The manual says that this allows for public access to the router, that's why we're not using that option. However, with this option I can still set up a WEP key, does that mean that people will have to provide a WEP key to connect? So we don't get neighbours and such connecting...)

* Shared Key (Current Setting)

* WPA

* WPA-PSK

* 802.1x


All these option is a bit confusing to me. Not really sure what they all mean or do. Even the manual doesn't really help me out much either.

---

### Post by ThomThom on 2005-11-12
The network card is a Skyr@cer Pro PCI 154. I'll see if I can post the result of sudo lshw -C network. Will have to transfer it from my desktop (where Ubuntu is installed and to the laptop I'm using here now to access the internet)

Btw, Windows XP connects fine to the network with a Shared WEP key so I know that it's not a limitation of the card.

---

### Post by ThomThom on 2005-11-12
Result from "sudo lshw -C network"

```

  *-network:0
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@02:02.0
       logical name: ath0
       version: 01
       serial: 00:03:2f:20:ad:41
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERI MENTAL) ip=192.168.2.80 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fe8f0000-fe8fffff irq:17
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 02
       serial: 00:07:e9:4c:dc:a0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion =3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10M B/s
       resources: iomemory:fe8df000-fe8dffff ioport:cf40-cf7f irq:20


```

---

### Post by Lambert on 2005-11-12
wep and wpa are two different security methods. wep was the original and wpa is replacing wep. wpa is more secure but it's an incomplete standard. It's currently a work in progress.

When you go into system>admin>network manager, you don't even get an option to use wpa, it's only wep. 

with wep you stil have to enter the key to get access and it does offer a decent layer of protection.

Your card is using the madwifi driver (atheros chipset) so I don't even think you can use wpa with out a lot of configuring. I tried for a day, gave up and went back to wep. If you want to use wpa, you will have to install wpasupplicant, do a search for that to see how to set it up. try here in the forums, google, or the wiki.

Another layer you can add to protect you from neighbors is not to broadcast your router signal. Not sure about your router but I believe most routers today offer this option. 

So to clarify
1. download wpasupplicant and search to see if you can get your network up and running with wpa
or
2. back your router to a wep setting

edit-something else I just saw was something called hostapd. It's in the repositories so you can install this and try to get wpa set up. I know nothing about it but you can google this term also or look for the documentation to learn more about it.

if you decide to go with wpa and get wpa up and working, come back and post the steps you took as I'd be interested.

---

### Post by emperor on 2005-11-12
[quote=ThomThom]Result from "sudo lshw -C network"

```

  *-network:0
     ....
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERI MENTAL) ip=192.168.2.80 multicast=yes wireless=IEEE 802.11g
  .....

```[/quote]

There is definitely no link ocurring as there should be a statement like: "link=yes" in the above statement.

Your card is reported to work in Ubuntu per: [http://madwifi.org/wiki/Compatibility#SKYRCERPROPCI154](http://madwifi.org/wiki/Compatibility#SKYRCERPROPCI154)

Your card also has the same chipset (AR5212) as the D-link (DWL-G650) card I installed in my daughters laptop and Lambert is using. 

These links should be helpful:
[http://madwifi.org/wiki/UserDocs/SimpleWEPClient](http://madwifi.org/wiki/UserDocs/SimpleWEPClient)
[http://madwifi.org/wiki/UserDocs/AuthorizationFailed](http://madwifi.org/wiki/UserDocs/AuthorizationFailed)

You might try iwconfig manually too, experiementing with the order as indicated in the above link. If the order is an issue, then change the order in the "interfaces" file.

"iwconfig" will set a range of wireless settings, for a list of all possible:

 iwconfig --help

Sometimes the no "link" problem can be cause by the "default" gateway not being set.

---

### Post by ThomThom on 2005-11-12
hm.. It's working! I think it was because I set the Network Authentication to Open instead of Shared. And I then reset the network settings in Ubuntu to the default. And now it's working. wicked! I can now get this baby rolling.

Thanks for all your help guys!

---

