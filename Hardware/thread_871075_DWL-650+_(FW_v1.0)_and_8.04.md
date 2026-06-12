---
title: "DWL-650+ (FW v1.0) and 8.04"
date: 2008-07-26
forum: Hardware
---

### Post by taarhaug on 2008-07-26
hi,

been close to ten years since I last installed linux...

Installing Ubuntu Desktop 8.04 was OK till I tried my cardbus wireless card... The card appears to be detected OK, but once I try to connect to my access point, I first get a dialog telling me to type the encryption password. If I retype (the correct) password odd behavior is observed: system freeze, loss of keyboard, network hang, etc.  I have tried several connection schemes but it appears that I am not able to connect to my access point regardless.

I have two questions:

1) How do I debug this?  I read in the forum that ifconfig might be of interest:

wlan0     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          inet6 addr: fe80::280:c8ff:feb0:e75e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:11 Base address:0x3c00

but besides this I have no clue. I read up on some ndiswrapper but found the topic a bit too advanced.

2) The card is 802.11b so I could afford a new g/n... any suggestions that would work under ubuntu? (I dislike DLINK and like LINKSYS).

Yours,

Thor Anders Aarhaug

---

### Post by JoesCat on 2008-07-26
I just wish to let you know that I had troubles running 128bit WEP on a DWL-G630 and had to drop down to 64bit WEP.
This was under Windows 98, and therefore never attempted any higher encryption. Possible bug in software or in driver.

The ndiswrapper worked fine for 64bit but untested for 128bit using puppy linux since the laptop was underpowered for anything much more advanced.

You may want to check out the various encryptions or state which version/type of encryption you are using (just in case the one you happen to be using right now may be the buggy version).

Thanks,
Jose

---

### Post by taarhaug on 2008-07-26
> **JoesCat said:**
> I just wish to let you know that I had troubles running 128bit WEP on a DWL-G630 and had to drop down to 64bit WEP.
This was under Windows 98, and therefore never attempted any higher encryption. Possible bug in software or in driver.

The ndiswrapper worked fine for 64bit but untested for 128bit using puppy linux since the laptop was underpowered for anything much more advanced.

You may want to check out the various encryptions or state which version/type of encryption you are using (just in case the one you happen to be using right now may be the buggy version).

Thanks,
Jose

I am currently using WEP 128bit Hex and this card has worked well under XP. I tried to change the open/shared option for WEP, turned off encryption, turned on SSID broadcast. But still I didn't get connected.

Thor

---

### Post by JoesCat on 2008-07-26
> But still I didn't get connected.

The problem I had with 128bit on windows98 was that you would have to reload the 128bit key every time you rebooted. The software was poorly written and forgot to keep your keys, so I ended up going with 64bit.

In terms of 64bit encryption, it appears to work okay.
I filled in all 4 keys (Key1, Key2, Key3, Key4) using HEX on the puppylinux to match the HEX on the router because the passphrase done on the router and the passphrase done on the wireless card software return different values.
The router is a LinkSys while the card is DLink which shouldn't be a problem since they are both using 802.11g in this case.

I'm assuming that since you already have access with XP, then your router already has your MAC, so make sure your router accepts your wireless card MAC

If you live in a busy neighbourhood (lots of routers around), you may want to verify that you are on a channel of your own and not using/sharing a channel with others, many users seem to leave it at default (6) or put it at max (11) or min (1), so I suggest you try put it on another channel such as 4 or 8. If your neighbourhood is particularly busy, I'd have the router broadcast a beacon 10x more frequently.

SSID broadcast would normally be done by the router, not your laptop.

if you are still having troubles connecting, I'd suggest trying the puppy linux since it's small. Use ndiswrapper and use the XP drivers (I think it's 2 files of interest a *.inf and a *.sys which should be located on the XP subdirectory for the DWL-630 install CD).

---

### Post by taarhaug on 2008-07-28
Apparently, my version of the card (A1) requires madwifi rather than acx100... if only I can find a way to install the correct drivers... :)

Thor

---

### Post by taarhaug on 2008-07-30
well,  I solved it myself. The driver was OK, it's just the NetworkManager that causes trouble... 

I chose Network Settings and unchecked Roaming.  Set the parameters as best as I could there (ssid, wep). Then I used wlanconfig to set the essid, reset the key and after a ifdown and ifup wlan0 the network was up and running.

The DWL-650+ A1 FW1.0 is in other words properly recognized and the interface installed at insertion.

Thor

---

