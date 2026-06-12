---
title: "Skystar2 problems"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by ChriX on 2006-02-19
Just found my old Technisat Skystar2 card last night so I thought I would give it a go. There seems to be a few guides about, both on this forum and elsewhere but none that I have found address the problem I'm having.

I'm at the same place now after a few hours of playing around as I was when I first plugged the card in.

dmseg output:
```
[4294690.502000] drivers/media/dvb/b2c2/skystar2.c: FlexCopII(rev.130) chip found
[4294690.502000] drivers/media/dvb/b2c2/skystar2.c: the chip has 6 hardware filters
[4294691.060000] DVB: registering new adapter (SkyStar2).
[4294691.252000] i2c_readbytes: i2c read error (addr 0a, err == -121)
[4294691.842000] mt352_read_register: readreg error (reg=127, ret==-121)
[4294691.970000] mt312_read: ret == -121
[4294691.970000] skystar2: A frontend driver was not found for device 13d0/2103 subsystem 13d0/2103

...

[4294702.893000] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
```

lspci:
```
0000:01:06.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 01)

```

lsmod:
```

b2c2_flexcop_pci        7636  0
b2c2_flexcop           27084  1 b2c2_flexcop_pci
stv0297                 9408  1 b2c2_flexcop
skystar2               30532  0
dvb_core               82088  2 b2c2_flexcop,skystar2
mt352                   6788  2 b2c2_flexcop,skystar2
evdev                   9728  0
stv0299                11656  2 b2c2_flexcop,skystar2
nxt2002                 9348  2 b2c2_flexcop,skystar2
firmware_class         10240  3 b2c2_flexcop,skystar2,nxt2002
mt312                   8388  2 b2c2_flexcop,skystar2
i2c_core               21328  9 i2c_acpi_ec,b2c2_flexcop,stv0297,i2c_nforce2,skystar2,mt352,stv0299,nxt2002,mt312

```

The problem lies (I think) with the frontend, as it isn't able to find a driver, I can't progress any further with the guides, as all the dvb-utils can't find a frontend to use. From what i've seen this card should be using mt312, it's a fairly old one from EOL, but as you can see the modules are loaded. 

Any ideas?

Thanks

---

### Post by tog on 2006-07-09
Ok, I too have similar problems, but a more basic one. I can't seem to find the skystar2.ko module at all. My kernel is 2.6.15-25-386. The card was working properly in the the older kernels, but now the modules is missing. I recompiled the modules from linuxtv.org, but that too doesn't seem to have the module. Here is the output from my dmesg:
[17179595.896000] nxt200x: NXT2002 Detected
[17179595.896000] b2c2-flexcop: found the nxt2002 at i2c address: 0x0a
[17179662.340000] nxt2002: Waiting for firmware upload (dvb-fe-nxt2002.fw)...
[17179662.436000] nxt2002: Waiting for firmware upload(2)...
[17179662.720000] nxt2002: Firmware upload complete
[17179663.040000] nxt200x: Timeout waiting for nxt200x to stop. This is ok after firmware upload.

What kernel are you using? 

Tog

---

### Post by tog on 2006-07-10
Ok. Looks like the latest Kernels have replaced the skystar2 module with flexcop. 

Tog

---

