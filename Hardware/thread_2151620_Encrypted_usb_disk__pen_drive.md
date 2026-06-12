---
title: "Encrypted usb disk / pen drive"
date: 2013-06-05
forum: Hardware
---

### Post by naxtek on 2013-06-05
Hi,

My girlfriend is a teacher.  She uses her own Ubuntu laptop at home and the school's Windows computers at work, regularly transferring the usual mess of Microsoft Office documents between both.

They have recently told her that she must use an encrypted usb disk to transfer files between home and work in order to ensure sensitive data about children is secure, which I think is understandable and commendable.  In practice though they gave her something which doesn't work with Ubuntu - an Integral Crypto USB disk.  It doesn't claim to be compatible, but I tried it anyway and unsurprisingly, it didn't work.  I tried Googling for some assistance, but no joy.

They have told her she can get her own, so I've been looking at options.  The requirements are:

1) It must be encrypted
2) It must work with Ubuntu
3) It must work on a Windows machine without needing anything installed, since all the machines at work are locked down*

The only one I have found so far which should work is this physical encrypted pen drive with a keypad on the disk itself: [http://www.amazon.co.uk/Corsair-CMFPLA8GB-256-Bit-Encryption-Flash/dp/B003809LBS/ref=sr_1_3?ie=UTF8&qid=1370428156&sr=8-3&keywords=usb+padlock](http://www.amazon.co.uk/Corsair-CMFPLA8GB-256-Bit-Encryption-Flash/dp/B003809LBS/ref=sr_1_3?ie=UTF8&qid=1370428156&sr=8-3&keywords=usb+padlock)

Can anyone suggest any alternatives which fit the bill?  Is there no software encryption which might work?


[SIZE=1]* I realise that most encrypted disks require something to be installed, including the Integral Crypto they gave her, so I am not sure if that's absolutely true.  My guess is they got their IT monkey/administrator to pre-install the software for the Integral so it "just works" and they probably don't want to mess about making the same monkey install something else on every machine just so my girlfriend can be awkward and use something different.
[/SIZE]

---

### Post by darekch on 2013-06-05
You can try LUKS. In Windows you can try use LUKS via FreeOTFE (admin permissions needed). Little info:
[http://www.mayrhofer.eu.org/encrypted-container-linux-and-windows](http://www.mayrhofer.eu.org/encrypted-container-linux-and-windows)
Note that I didn't use it. Don't know if such mixture (Luks, FreeOTFE) will work in the real world.

The other solution would be encrypted dropbox maybe?

Interesting how secure is that device? Due to it's keypad password will be usually short. Thus if this device can be unlocked programmatically (via OS), then this device can be brute forced easily I think.

Give a note if you will find some working solution.

---

