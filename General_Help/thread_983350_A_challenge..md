---
title: "A challenge."
date: 2008-11-15
forum: General Help
---

### Post by poo_22 on 2008-11-15
if i have two computers, one with wifi and ethernet, and one with only ethernet, and two routers one of wich is wireless: How can i get both computers to have internet if they cannot be connected to the wireless router with a cable, and if the non-wireless router cannot be connected to a modem?

---

### Post by Bigneil on 2008-11-15
This may not be helpful, but, sell them on ebay and buy a wireless modem router with an ethernet connection on the back.

---

### Post by poo_22 on 2008-11-15
> **Bigneil said:**
> This may not be helpful, but, sell them on ebay and buy a wireless modem router with an ethernet connection on the back.

haha I like that... i might just settle for a usb dongle. but meanwhile....

---

### Post by ibuclaw on 2008-11-15
Answer:
Connect the second computer (ethernet) to the first computer (ethernet/wireless) via ethernet and setup the first computer to act as a gateway/proxy for the second computer to share internet access with.

If you so wish, you could use the wired router to connect the two computers together.

:)

Now... I'll look up how to implement that (It can be done with Windows, so it can be done with Linux)

Regards
Iain

---

### Post by madsmeg on 2008-11-15
personally, if it was me, I would rewire the house so I COULD do what you want to do, and save on any future fuss.

---

### Post by poo_22 on 2008-11-15
thanks Iain very helpful response! please post any insight on how to that if you find it. I think this is exactly what i was looking for.

---

### Post by Mardoct909 on 2008-11-15
Have a simple topology of: Internet->Modem->Router->Long Cables->Computers.

---

### Post by iponeverything on 2008-11-15
```

iptables -t nat -A POSTROUTING -s  192.168.1.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Add something like this to your rc.local where the network address block to be masq is correct for your network.  The above will masq 192.168.1.1 - 192.168.1.254

clients:
Add opendns server address to the /etc/resolv.conf and have them use the address of the masq box for there default gw.

If the second computer is connected directly to first use a X-over Ethernet cable.

---

### Post by poo_22 on 2008-11-15
> **iponeverything said:**
> ```

iptables -t nat -A POSTROUTING -s  192.168.1.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Add something like this to your rc.local where the network address block to be masq is correct for your network.  The above will masq 192.168.1.1 - 192.168.1.254


that was a bit over my head, could you please explain in a little more detail what you are doing there?

> 
Add opendns server address to the /etc/resolv.conf and have them use the address of the masq box for there default gw.


Ok so that will make the client box use the other computer as a router/default gateway, but how does it get assigned an ip address?

---

### Post by iponeverything on 2008-11-16
```
sudo iptables -t nat -A POSTROUTING -s  192.168.1.0/24 -j MASQUERADE
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
```

I added sudo to the above command. The first one tells your box to NAT anything going out that is in the 192.168.1.0/24 range. The second command just tells your box to forward packets.
> 
Ok so that will make the client box use the other computer as a router/default gateway, but how does it get assigned an ip address?

You either have to assign a static IP to client or setup dhcp on main machine.

---

### Post by poo_22 on 2008-11-16
How can i assign a static ip to the client? (dns would be pointless: there is only one client)

---

### Post by poo_22 on 2008-11-16
bump

---

### Post by poo_22 on 2008-11-16
bump

---

### Post by TeXtonyx on 2008-11-16
Here is a cheap idea to try. Buy a phoneline splitter (I've never
needed a filter) and connect it to the phone line. I think you'll
need another dsl phone/dsl splitter. Make two sets of dsl setups,
and put the wireless router cable into one and wired router cable
into the other, they both have a capabiliyy to connect to the telephone
line. Use the computer which can do wireless with the wireless
router and the computer which is wired with the wired only router.

This works with multiple phones on one telephone line, but I only
use one phone at a time and yes there is enough current to drive it
even though it takes 30 ft. long phone line wires.

I'm not sure whether the dsl part of the phone line will support
both computers connecting to the internet at the same time. You
didn't mention that as a requirement. It is easy enough to unplug
the cable to the wired router and switch. Whether they will both
work at the same time without conflict, I don't know, but either
one at a time should work. You might need two phone line splitters.

I have only one telephone wall jack, so I have to take extreme measures.
If you have two telephone wall jacks, this should be even easier.
My phone line doesn't know there is a splitter and neither does the
dsl part of the line know it wire is split. Just, as I said, I don't
know whether the dsl part will support concurrent transmissions.

---

