---
title: "How to obtain Wireless MAC Address?"
date: 2010-07-22
forum: Hardware
---

### Post by behyc on 2010-07-22
Hi,

I just installed Ubuntu and I love it very much. Unfortunately, I'd like to add the wireless mac address into the wireless router but I'm not sure where I could get that information from Ubuntu.

Can anyone please guide me the location on obtaining the Wireless MAC Address?

---

### Post by AlphaLexman on 2010-07-22
It SHOULD be on the bottom of the wireless device. Even a laptop with built-in wireless has a mac-address sticker.

---

### Post by behyc on 2010-07-22
> **AlphaLexman said:**
> It SHOULD be on the bottom of the wireless device. Even a laptop with built-in wireless has a mac-address sticker.

Thanks for replying. But I'd like to know from ubuntu OS itself where can I find it instead of physically looking for it. I'm pretty noob in this. :oops:

---

### Post by IcarusR on 2010-07-22
Type the following in a terminal & you will see details of your network cards including mac address (hardware address)

```
ifconfig
```

---

### Post by bichopro on 2010-07-22
sorry my ban English. right click on the wireless icon an click on info

---

### Post by AlphaLexman on 2010-07-22
Do you have permission to login to the wireless router? The router itself will tell you. 
I think getting the MAC address from the kernel or software is pretty difficult.

---

### Post by behyc on 2010-07-22
> **IcarusR said:**
> Type the following in a terminal & you will see details of your network cards including mac address (hardware address)

```
ifconfig
```

Thanks IcarusR. Unfortunately I'm not sure where the Terminal is located...:(

> **bichopro said:**
> sorry my ban English. right click on the wireless icon an click on info

bichopro, thanks...i found it~ :)

> **AlphaLexman said:**
> Do you have permission to login to the wireless router? The router itself will tell you. 
I think getting the MAC address from the kernel or software is pretty difficult.

AlphaLexman, I have the login permission unfortunately there's a whole bunch of mac address listed there already for all my wireless devices at home hence i'd like to make sure which one is the one for my netbook.

All, thanks for your prompt reply...I'm seriously looking forward in learning more of Ubuntu. I'm sorry if I had ask a silly question. Anyway, I'd like to thank you guys again for replying me. :D

---

### Post by AlphaLexman on 2010-07-22
Technically, ifconfig is used for eth0 (wired) ports, and iwconfig is better for wireless ports.

At least on my wireless router (D-link), I have a tab, Status, and a sub-menu, Wireless... which gives all the MAC addresses of all systems connected to the router.

---

