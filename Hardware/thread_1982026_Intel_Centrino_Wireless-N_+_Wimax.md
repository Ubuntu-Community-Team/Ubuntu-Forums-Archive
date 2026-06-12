---
title: "Intel Centrino Wireless-N + Wimax"
date: 2012-05-17
forum: Hardware
---

### Post by SyntheticShield on 2012-05-17
Im getting ready to purchase a Dell Inspiron 17R 7110.  One of the things I a bent on getting is the WiMax capability.  I am with Sprint as my cell provider.

In looking at the cards, just in case I could not find one already with WiMax I found the Intel Centrino Wireless-N + WiMAX 6150 and also WiMAX 6250.  That prompted some questions I hope someone here can answer.

1.  Will the 6250 work with the Dell 17R?
2.  What are the differences between the two cards and are they significant?

I may be reading the information incorrectly so forgive me if I am off base here.  But in looking at the info provided by Intel it looks like the 6250 card is a 2x2 card and the 6150 is not.  Am I correct in assuming that that means both the WiFi and WiMAX can operate at the same time, whereas on the 6150 it cannot?  Thats not a big deal really and Im not sure why you would want to run both at the same time.  That cant be good for battery life.

The only other major difference I see is that the 6250 uses the Wave 2 WiMAX and covers the 3.5Ghz band whereas the 6150 only covers the 2.3 & 2.5GHz bands.

If the 6250 will work then I will just buy the card separately and install it myself.

Oh, one other thing, I assume the bluetooth capability is provided by a separate card?  I know some WiFi cards from Intel have bluetooth built in but I dont see that here.

Thanks for any assistance.

---

### Post by idoitprone on 2012-05-17
> **SyntheticShield said:**
> Im getting ready to purchase a Dell Inspiron 17R 7110.  One of the things I a bent on getting is the WiMax capability.  I am with Sprint as my cell provider.

In looking at the cards, just in case I could not find one already with WiMax I found the Intel Centrino Wireless-N + WiMAX 6150 and also WiMAX 6250.  That prompted some questions I hope someone here can answer.

1.  Will the 6250 work with the Dell 17R?
2.  What are the differences between the two cards and are they significant?

I may be reading the information incorrectly so forgive me if I am off base here.  But in looking at the info provided by Intel it looks like the 6250 card is a 2x2 card and the 6150 is not.  Am I correct in assuming that that means both the WiFi and WiMAX can operate at the same time, whereas on the 6150 it cannot?  Thats not a big deal really and Im not sure why you would want to run both at the same time.  That cant be good for battery life.

The only other major difference I see is that the 6250 uses the Wave 2 WiMAX and covers the 3.5Ghz band whereas the 6150 only covers the 2.3 & 2.5GHz bands.

If the 6250 will work then I will just buy the card separately and install it myself.

Oh, one other thing, I assume the bluetooth capability is provided by a separate card?  I know some WiFi cards from Intel have bluetooth built in but I dont see that here.

Thanks for any assistance.

wimax does not work

```
lspci -nnk | grep -iA 2 network
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1301]
    Kernel driver in use: iwlwifi
```

```
uname -a
Linux localhost.localdomain 3.3.4-5.fc17.x86_64 #1 SMP Mon May 7 17:29:34 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

does not work with kernel less than 2.6.35

nuff said

---

### Post by SyntheticShield on 2012-05-17
Okay?

I will be running Ubuntu 12.04 which is currently on kernel 3.2 something?  So, to be clear, you're saying its a waste period?

---

### Post by idoitprone on 2012-05-17
> **SyntheticShield said:**
> Okay?

I will be running Ubuntu 12.04 which is currently on kernel 3.2 something?  So, to be clear, you're saying its a waste period?

3.2 > 2.6.35 

it should work on ubuntu 12.04

It should work it does not have a reason not to

Do watever you want. please bear in mind choose the band based on your router

wimax in general does not work on linux. it a  windows only feature

---

