---
title: "Problems with Intel® Next-Gen Wireless-N Mini-PCI Card"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by Aybara on 2008-02-13
I have the mentioned card on my Ubuntu Gutsy, and I have a problem with it.

I see the available wireless networks, and I can connect to mine. When I try to use the connection though, it dies and refuses to come back until I reboot my pc.

Edit: lspci tells me it's called Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection. Maybe that means more to some of you

---

### Post by jan quark on 2008-02-14
try to establish a connection not by roaming mode but by manual configuration

can you post also the output of these terminal commands

```
iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```
```

lspci
```

```
sudo lshw -C network
```

here is also a guide how to enable your card 
although it is for fiesty it should also work with gutsy,
but first we must make sure if your card dirvers are perhaps installed correctly and something different is the cause for the bad connection

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29)

---

### Post by Aybara on 2008-02-14
Short story long: the Jensen router I had was 4-5 years old, so I decided to get a new one today. I have a ps3 that I want to stream to, so I can use the extra speed. Anyway, with the new router my wireless is working :-)

---

