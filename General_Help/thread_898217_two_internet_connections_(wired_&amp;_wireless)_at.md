---
title: "two internet connections (wired &amp; wireless) at same time"
date: 2008-08-23
forum: General Help
---

### Post by malanco on 2008-08-23
hi guys, ill like to have to internet connections at the same time, not to bound or something like that, i want to have my wireless connected and also my wire connection, this is because ill give my virtual machine (micro$oft xp) the wireless so i can download torrents there and do not affect my other connection that is to another AP, so is there a way to do this??, i xp i just connect to both and then in vmware workstation i assign the nic to my vm (wireless nic), but here i have wicd, and when i want to connect to the wired connection the wireless one gets disconnected

Any help will be greatly appreciated!! :)

---

### Post by Washer on 2008-08-24
i think you can only do it manually. 

sudo ifconfig eth<whatever> <IPaddress> up

---

### Post by malanco on 2009-02-16
the problem here is that i get differrent ip addresses but, i have issues with networking.

---

### Post by malanco on 2009-02-16
sorry for my bad english, i mean i get two different ip adresses both in the same range 192.168.2.X, and if i want to reach ping any host or reach it there is no way, only if i give down the wlan0 interface.

thanks

---

### Post by handy on 2009-02-17
This is probably more than you want to know, but anyway:

If you can get hold of an old PII (as they use such a small amount of electricity) I use a PIII, you can install [*_IPCop_*]("http://www.ipcop.org/") a brilliant & easy to set up Firewall, router (& other available services) which will allow you to have multiple internet ins & you can map where they go.

---

