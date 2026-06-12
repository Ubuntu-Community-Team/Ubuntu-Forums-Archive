---
title: "Ethernet controller stopped working"
date: 2011-04-27
forum: Hardware
---

### Post by NoJamNoMusic on 2011-04-27
Hello.
Yesterday I was working on the pc(ethernet working fine). I closed it, my bro opens it 10mins later and there was no ethernet connection.

Im trying to determine the source of the problem.
It is not the cable nor the router nor the ISP since Im using them from the very Laptop Im making this thread.

I want to know whether the Network card is dead or whether there is a motherboard malfuction.

(Sorry for not having the whole output. Im typing only what I thought is important)
```
sudo lspci | grep -i eth
```

```
Ethernet controller: Realtek semiconductor Co. Ltd. RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev03)

```


```
ifconfig
```

```
Link encap:Ethernet HWaddr: 40:61:86:34:41:84
...
```


```
sudo lshw -C network
```

```
...
psysical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: 03
...
```


The lights at the Ethernet input are not on.
I have also logged in Windows XP and the same issues remain.
Any help will be appreciated.

---

### Post by Yellow Pasque on 2011-04-27
I would try disabling it and then enabling it in the BIOS.

---

### Post by MasterTech515 on 2011-04-27
> **NoJamNoMusic said:**
> Hello.
Yesterday I was working on the pc(ethernet working fine). I closed it, my bro opens it 10mins later and there was no ethernet connection.
 
The lights at the Ethernet input are not on.

 
If the lights are not on it means that either the card is dead or the driver is not working. Since the OS is recognizing the card, it means that the card is working. Check the driver and/or conflicts. Try re-installing the card and/or the cables.

---

### Post by NoJamNoMusic on 2011-04-28
All I could do from BIOS was first disable the LAN controller.
Then booted and entered Ubuntu 10.04
Then re-enabled the LAN controller(from BIOS), but the problem remains.
Is there any other option in the BIOS menu I missed?

---

