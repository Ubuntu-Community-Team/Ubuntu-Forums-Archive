---
title: "Asus M2N-E Motherboard, not 100% working"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by leona on 2007-05-21
This weekend I upgraded my machine to a 3800+ x2 AMD thingy using the [Asus M2N-E]("http://www.asus.com/products4.aspx?modelmenu=2&model=1181&l1=3&l2=101&l3=0"), nice and quick and only really did it cos the motherboard was given to me cheap and the cpu was cheap.

This stuff isn't brand new, the board was out last year for example, but I seem to be having problems getting it working well with Linux. Ubuntu  6.06.

Ok, so I've lost my hardware monitoring sensors, temps, fan speeds, gone, lm-sensors, will not detect anything, so I'm guessing it just not supported.  Ok that's only a nice thing, if it doesn't work its not the end of the world.

But this is a 'end of world thing' cos my major problem is that my sound doesn't work, I've got no output at all, according to the website its a ADI 1988 8-channel High Definition Audio CODEC
Seems partically Low / no def at the moment :(  

Can anyone help by pointing me in the right direction to get this sorted out? I did a quick search for my board on this forum but didn't get anything that could help me.

thanks.

---

### Post by apjone on 2007-05-21
try a lshw and check what is reported under multimedia. Try switching between esd / alsa and oss see if you can get anything. Also check that you are using the correct card in volume properties

---

### Post by leona on 2007-05-21
arr cool, I didn't know about that, I get this when I type sudo ishw

```

     *-multimedia
          description: Multimedia controller
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:fe024000-fe027fff irq:58

```
Now I'm no expert but I don't think that driver is correct?

Not sure what you mean by 
> 
Try switching between esd / alsa and oss see if you can get anything.

though, could you elaborate?

---

### Post by leona on 2007-05-21
Ok, this is bizare, the sound is now working, but I didn't DO anything! :) how odd.

---

### Post by nss0000 on 2007-05-21
BigL:

I'm running Dapperx64 on an ASUS_m2n. Neither LM_sensors nor sound nor onboard eth_port are supported. I use a SBx16 workalike soundcard and legacy NIC.

LM_sensors is another matter. No solution there I think.

nss
******

---

### Post by leona on 2007-05-21
Also 64bit Ubuntu 6.06 here, the network seems to work, does your 'ishw' output look similar to this?
```

  *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth1
          version: a2
          serial: 00:18:f3:fb:fa:f2
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=full ip=192.168.1.2 link=yes multicast=yes port=MII speed=100MB/s
          resources: iomemory:fe02a000-fe02afff ioport:b000-b007 iomemory:fe029000-fe0290ff iomemory:fe028000-fe02800f irq:66


```

---

