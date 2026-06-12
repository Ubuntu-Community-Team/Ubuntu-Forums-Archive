---
title: "Laptop overheating until crash on Ubuntu 13.04"
date: 2013-06-19
forum: Hardware
---

### Post by Solum on 2013-06-19
I installed Ubuntu 13.04 on my Vaio-Laptop a few weeks ago, and recently the overheating has become more and more of a problem. After half an hour it crosses 80°C, and a few minutes later the Laptop crashes and needs to cooldown before it can start again. While it is on the fan is running constantly.
I haven't found a solution by myself, so i'd appreciate your help :)

_PC Model:_ Vaio VPCEB3E1E/WI[U]
Graphics card:[/U] ATI Mobility Radeon HD 5470
                     Mobility Radeon HD 5000 Series
_CPU:_ Intel® Pentium(R) CPU P6100 @ 2.00GHz × 2
        Dual Core
        64-bit
_RAM:_ 4GB; 8GB maximum[U]
Chipset:[/U] [COLOR=#000000][FONT=Verdana]Mobile Intel HM55 Express
As far as I can tell it isn't an APU. Hybrid, not so sure.
[Here]("http://www.sony.co.uk/support/en/product/VPCEB3E1E_PI/specifications") are some more specs, should you want them :)
[/FONT][/COLOR]

---

### Post by QIII on 2013-06-19
Hello!

Can you give us a little bit of information about your hardware, particularly the CPU and graphics?

---

### Post by Solum on 2013-06-19
Ah, yes. Sorry, I forgot that ^^
As far as I know there are some problems with the Mobility Radeon card drivers which cause the system to increase the temperature by 25°, but I don't really know how to fix that :/

---

### Post by QIII on 2013-06-19
That is common.

Again, though, we need some detailed information about your hardware.

What series of ATi GPU?  Is this an APU?  Is this an Intel/ATi hybrid graphics arrangement?

Thanks!

---

### Post by Solum on 2013-06-19
I added a link to the Laptop's webpage. You should be able to find everything there :)

---

### Post by QIII on 2013-06-19
OK

Have you installed the proprietary fglrx driver?

---

### Post by Solum on 2013-06-20
Yes, but apparently it doesn't support my hardware.

---

### Post by QIII on 2013-06-20
That GPU should be supported, although sometimes the M GPUs are actually just overclocked versions of earlier chips.  You might find that in ATi's odd naming scheme, a 5470M is really an HD 4000 unit that is overclocked.

If you have the driver installed, could you please post the results of 

```
fglrxinfo
```

---

### Post by Yellow Pasque on 2013-06-20
The 5470 is not a rebadge and should be supported by fglrx/Catalyst:
[http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units#Mobility_Radeon_HD_5xxx_Series](http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units#Mobility_Radeon_HD_5xxx_Series)

---

### Post by QIII on 2013-06-21
Some of the M GPUs in the HD 5000 series are (some of them up through 5300), but in this case the chip is a Cedar so it is a real live HD 5000.

---

### Post by agillator on 2013-06-21
Don't overlook the obvious, either. Are your air vents clear, and if you prop the laptop up and put a fan on it, does the temp drop enough to let the computer run? If your computer is not particularly new that can indicate old thermal grease. This is probably not your problem in this case but is worth checking anyway since it is so easy.

---

