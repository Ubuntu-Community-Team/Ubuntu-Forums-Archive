---
title: "PC unable to boot, by pressing the start-button"
date: 2021-04-05
forum: Hardware
---

### Post by satimis on 2021-04-05
Hi all,

I have an old PC resting on shelve sometimes which I shall use it for testing installing cPanel.

Configuration:
CPU - AMD 8-core
HD - 1TB SSD
RAM - 2x4G 8G

Yesterday, I took it down, upgrading OS Ubuntu 18.04 to 20.04 and tested it without problem for 2~3 hours.  Today I couldn't start it, pressing the start-button without response.  Also I have tried using a screw-driver to shorten its connectors.  The green LED is on the motherboard.  Also there is USB power output.  I tested it with an USB light.

It is very strange to me.  Please advise where shall I start to check first.  Would it be the power supply problem?  Or CPU problem?  I have no spare CPU to check.

Please advise.  Thanks

Regards

---

### Post by Autodave on 2021-04-05
Most likely the power supply.  Next most likely would be the mother board.

I assume that you have checked wiring connections?

---

### Post by satimis on 2021-04-05
> **Autodave said:**
> Most likely the power supply.  Next most likely would be the mother board.
There is power output from the power supply.  I tested it by plugging a LED light to USB port.  It worked with the LED light on.  I have no spare power supply.  To replace it for checking I have to remove a power supply from another PC.

I have no idea checking the motherboard.  It looks quite funny to me.  Day before yesterday I have been working on this old PC for 2~3 hours, including rebooting several times

> 
I assume that you have checked wiring connections?
Yes, I have done it including unplugging RAM, connecting the connectors of Power-On switch with a screw driver without result.

---

### Post by CatKiller on 2021-04-06
I'd suggest the same components as Autodave, but *probably* reverse the likelihood. It could go either way. Obviously letting out the magic smoke would be a sign. 

> **satimis said:**
> There is power output from the power supply. 

That doesn't necessarily tell you much. The PSU provides power on multiple rails at different voltages. A failed PSU can still provide power on some but not others. 

The motherboard uses those rails to perform functions. A failed motherboard can still utilise power from some even if it's not able to utilise power from all of them.

Plus UEFI settings can cause a machine to fail to boot.

And although CPU and RAM don't generally fail as early as, say, capacitors in motherboards or PSUs, a history of overclocking or high temperatures can cause either to suddenly fail.

---

### Post by satimis on 2021-04-06
> **CatKiller said:**
> I'd suggest the same components as Autodave, but *probably* reverse the likelihood. It could go either way. Obviously letting out the magic smoke would be a sign. 

That doesn't necessarily tell you much. The PSU provides power on multiple rails at different voltages. A failed PSU can still provide power on some but not others. 

The motherboard uses those rails to perform functions. A failed motherboard can still utilise power from some even if it's not able to utilise power from all of them.

Plus UEFI settings can cause a machine to fail to boot.

And although CPU and RAM don't generally fail as early as, say, capacitors in motherboards or PSUs, a history of overclocking or high temperatures can cause either to suddenly fail.
Hello,

There is no problem on my old PC.

I have dismantled all components, thoroughly cleaned them with brush and vacuum cleaner and reassembled them.

Now my old PC can be started and booted.  It is still working strong.

$ inxi -C```

CPU:
  Topology: 8-Core model: AMD FX-8150 bits: 64 type: MCP L2 cache: 2048 KiB 
  Speed: 1487 MHz min/max: 1400/3600 MHz Core speeds (MHz): 1: 2084 2: 1470 
  3: 1416 4: 1409 5: 1950 6: 1886 7: 4064 8: 4247 
```

$ inxi -M```

Machine:
  Type: Desktop Mobo: ASUSTeK model: M5A97 R2.0 v: Rev 1.xx 
  serial: <superuser/root required> BIOS: American Megatrends v: 1302 
  date: 11/14/2012 
```

$ inxi -D```

Drives:
  Local Storage: total: 2.75 TiB used: 241.59 GiB (8.6%) 
  ID-1: /dev/sda vendor: Transcend model: TS1TSSD370 size: 953.87 GiB 
  ID-2: /dev/sdb vendor: Western Digital model: WD2002FAEX-007BA0 
  size: 1.82 TiB
``` 
  
$ sudo inxi -m```

Memory:
  RAM: total: 7.68 GiB used: 2.54 GiB (33.1%) 
  Array-1: capacity: 32 GiB slots: 4 EC: None 
  Device-1: DIMM0 size: 2 GiB speed: 1333 MT/s 
  Device-2: DIMM1 size: 2 GiB speed: 1333 MT/s 
  Device-3: DIMM2 size: 2 GiB speed: 1333 MT/s 
  Device-4: DIMM3 size: 2 GiB speed: 1333 MT/s 

```

Anyway, lot of thanks for your advice.

Regards

---

