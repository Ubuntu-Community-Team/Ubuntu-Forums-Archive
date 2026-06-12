---
title: "Wireless Encryption Problem"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by paul09 on 2007-04-15
I just got a new IBM ThinkPad T60 laptop and installed Feisty.  I can connect wirelessly to unencrypted networks, but would like to use WEP.  I have an Intel PRO/Wireless 3945ABG Network card, but cannot get it to connect to my 802.11g network with 128bit WEP.  It can detect the network and the card, but won't connect when i give it the key.  I also have a 802.11a network I would like to use if I can get it to connect.  My 802.11a network uses a 152bit WEP key.

Has anyone been able to fix a similar problem?  Thanks for any info you can share.

Here is some info that forums that I've read have asked for from other people:
```

$ dmesg | grep Wireless
[   17.160000] ipw3945: Intel(R) PRO/Wireless 3045 Network Connection driver for Linux, 1.2.0mp
[   17.684000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (Rev 02)

```

Please let me know if you need any more information.

---

### Post by drpaul on 2007-04-15
I assume that you know the key that your router is using [in hex format].

These are the steps in Edgy; I haven't installed Feisty so you'll have to translate.
Go to System Administration Networking
Click on the Wireless connection
Click on Properties
Put the network identifier in the top box
Put the key in the password box [I just type the continuous string of numbers with no separators]; choose type Hexadecimal
Enable the connection
Select OK and wait for the action

This worked for me.

PaUL

---

### Post by JerseyShoreComputer on 2007-04-15
I had similar issues with Edgy and connecting wirelessly with my Liinksys card. What I did was use the Synaptic Package manager and installed WiFi Radar. Once I did that, I was able to connect to my 128 bit WEP network. It's been working fine ever since.

Only problem is I cannot connect to WPA-SPK networks in my office. But at home with WEP it works just fine.

Good luck, hope this helps.

---

### Post by TheSandman on 2007-04-16
edit:
Mispost

---

### Post by kingy89 on 2007-04-16
If you are using multiply networks, are you making sure "Roaming Mode" is on?

(System -> Administrative -> Network -> Wireless -> Properties

---

