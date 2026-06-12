---
title: "eth0 dissappeared from lspci/ifconfig"
date: 2008-05-07
forum: Hardware
---

### Post by cooteian on 2008-05-07
I'm using a Dell e1505 running hardy, but it happened with gutsy as well, and my eth0 interface was working fine, and then seemingly without incident stopped working and did not appear in lspci or ifconfig. 

The only thing I can think of is at or about that time, I installed XP for a short time and when I was installing drivers for the machine, I installed one for the firewire port (a Ricoh) which did not work and even worse, when I tried to uninstall the driver, the computer would go to the blue screen of death. However, the firewire port shows up in lspci now. I also upgraded the BIOS at that time, but have since reverted to the old BIOS. 

When I plug into the eth0 port, the two lights, which should show green, show orange. 

I thought the eth0 port had just gone bad, but then the port on my Dell D600 (running hardy xubuntu) also went, so I got suspicious and wondered if anyone else has had the same or similar problem. 

Thanks, 

Ian

---

### Post by tamoneya on 2008-05-07
```
sudo ifconfig eth0 up
ifconfig
```
Does this fix the problem

---

### Post by cooteian on 2008-05-07
No, I should have mentioned that. 

/etc/network/interfaces looks like this:
auto lo
iface lo inet loopback

There definitely used to be an entry for etho. 

I also should mention that I am using a fresh install of Hardy and just to be on the safe side, I backed up everything and formatted the entire drive (previously I had a / and a /home partition. The /home partition I wouldn't format on a reinstall).

If there's anything else I can tell you about it let me know. It's not a huge problem, I just keep the ndiswrapper debs close and I use wireless. But it would be nice to get eth0 back. 

Thanks

Ian

---

### Post by tamoneya on 2008-05-07
you should be fine there.  That is identical to my /etc/network/interfaces and i have eth0 working fine.  As well as eth1 actually.

---

### Post by cooteian on 2008-05-07
Tamoneya, any idea why eth0 would stop showing up in lscpi? That is what seems most strange to me. I don't know what would cause that.

---

### Post by juan@forum on 2008-05-07
add this to /etc/network/interfaces

if you use DHCP
> 
auto eth0
iface eth0 inet dhcp


or if you use static configuration something like this

> 
auto eth0
iface eth0 inet static
   address 192.168.100.20
   network 192.168.100.0
   gateway 192.168.100.1



also check your nameserver resolver.

---

### Post by cooteian on 2008-05-08
juan@forum,

I added the lines to my /etc/network/interfaces (they used to be there, but have disappeared since I lost my ethernet controller from lspci). Then I ran

ian@ian:~$ sudo ifup -a
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.


As for the nameservice resolver, what exactly is that, and how would I check it?

---

### Post by cooteian on 2008-06-03
I recently spoke to the IT guy at work, he is unfamiliar with linux but he said that if the lights are coming on for the ethernet port (they show orange and red now but used to show green when it was working) then it is not a BIOS issue and is probably related to the driver. My question is, how can I tell if it's a driver issue? And if it is, how do I reinstall/fix the driver?

---

### Post by cooteian on 2008-06-10
I googled around a bit and found that I have a broadcom 440x 10/100 integrated controller. The linux drivers listed for this are either b44 or tg3. I modprobed both of them, they both show up in lsmod. I restarted /etc/init.d/networking. However, the broadcom 440x nic didn't show up in lspci. 

So, I rebooted, found out that the b44 and tg3 drivers failed to load. So I added them to /etc/modules and rebooted again. lsmod showed the drivers, but lspci did not show the card. 

I am completely at a loss.

---

### Post by Phloston on 2008-11-10
I had exactly the same problem. Mine was solved by removing the ethernet card and reinserting it. Possibly a part of the problem was that some pins on the card was touched by a cable (not very likely though, since the cable had insulation)

---

### Post by cooteian on 2008-11-10
Since my last post I have found that the smart card reader and the firewire port are all having problems. I installed XP (because my wife doesn't like mac os x, so now I am stuck using the mac, I certainly miss ubuntu) and in the device manager, there were a bunch of errors for the smart card reader and the firewire port. I disabled them in bios and she uses wireless only. 

I don't think I can remove the ethernet card, but I haven't dug that deeply into the machine. I suspect something like what you mentioned, a short or physical malfunction of the hardware. If I get a chance to dismantle her machine, I'll have a look. But she doesn't like me doing major surgery on it as it tends to take longer than expected. 

Thanks for the input, though.

---

