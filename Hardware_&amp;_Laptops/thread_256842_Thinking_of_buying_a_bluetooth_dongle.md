---
title: "Thinking of buying a bluetooth dongle"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by rama on 2006-09-13
... so I was wandering if a list of compatible bluetooth devices exists... 

I am thinking of buying a bluetooth headset as well and combine the two of them to talk with skype. Has anyone done that using ubuntu? PS: I m guessing that the brand of the headset does not matter since it only "talks" to the OS via a standard protocol.

---

### Post by wieman01 on 2006-09-13
Yes, there is a list but it's fairly outdated as far as the models are concerned but is still valid with regard to the chip-sets. I am using a Billionton bluetooth dongle and it works great. You may try this brand as well, but check it out yourself:

[http://www.holtmann.org/linux/bluetooth/features.html]("http://www.holtmann.org/linux/bluetooth/features.html")

The brand of the headset matters... unfortunately. But here are two types that works well for me (using Skype to make phone calls):

1. Plantronics 590 (rather expensive headset)
2. Logitech HS02-V05

Hope this helps.

---

### Post by rama on 2006-09-15
First of all thx for the reply. The thing is that I dont understand how the brand of the headset matters since the pc wont have to load drivers or something for that. Isnt that right?

---

### Post by wieman01 on 2006-09-15
> **rama said:**
> First of all thx for the reply. The thing is that I dont understand how the brand of the headset matters since the pc wont have to load drivers or something for that. Isnt that right?
That's a good question. But I have tried 4 bluetooth headset (got a few from friends) and I could get 2 out of 4 working with Ubuntu. And I have seen other posts from users confirming that. But give it a try yourself, I cannot give you a scientific or bullet-proof answer to that.

---

### Post by dario_751 on 2006-09-18
Hello wieman01

I have (almost) the same combination of dongle and headset: Billionton BT and Logitech HS02-V07. But in my IBM T42 it doesn't work :-(
My XP (SP2) recongnizes the logitech headset as a BT device, passkey works, etc. The problem is there are no services available for this device....
Do you know what might be a problem?
Thx in advance,

Dario

---

### Post by wieman01 on 2006-09-18
Yes, same problem with my Logitech device. It's there by all means, but somehow "invisible". Use Windows to figure out the MAC address of your device and try to connect to it using bluetooth tools under Linux. Although the system may not "see" your headset, you can connect to it when you give it the MAC address.

Example:
> btsco -v 00:0D:44:2E:C6:DF

---

### Post by freddy metz on 2006-09-18
so does the bluetooth usb stick's brand matter aswell?

---

### Post by wieman01 on 2006-09-18
> **freddy metz said:**
> so does the bluetooth usb stick's brand matter aswell?
It somehow does. But I cannot tell you anything beyond what I have experienced because nobody else could confirm it yet. Nonetheless 2 out of 4 headsets would not connect / work under Linux, so I am assuming the brand matters. 

Logitech shoul be generally fine I guess. But try yourself. And bear in mind what I have highlighted in my previous post (headseats _feigning_ death).

---

### Post by rama on 2006-12-03
The asus wl-btd202 did the trick as far as the pc is concerned ... Works great. I 'll get back with more info once I by a headset, or a handsfree device.

---

