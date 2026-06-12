---
title: "My nb is hot!!!"
date: 2009-10-11
forum: Hardware
---

### Post by achiola on 2009-10-11
Hi all.

Is beggin with ubuntu 8.04, now I have ubuntu 9.10:
```

achiola@achiola-laptop:~$ uname -a
Linux achiola-laptop 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:06:40 UTC 2009 x86_64 GNU/Linux

```
 every time I turn on or restart my notebook, the microprocessor temperature rises to the clouds ..

I just restart and the temperature reached:
```

achiola@achiola-laptop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp: +106.0°C                                    
Core0 Temp: +106.0°C                                    
Core1 Temp: +102.0°C                                    
Core1 Temp: +110.0°C            

```

My notebook is a compaq F756LA.

Now, my solutiion was install the "Frequency monitor" and force the clock to 800 mhz.


But, because the temperature rises like this??? any idea?

TIA
Abel.

---

### Post by savagenator on 2009-10-11
I found that the temperature will usually stay about those temps. I have a huge heatsink on my AMD, and it still goes over 110 on individual cores.

On my old mobo, my something or other was 69-71 celcius!

---

### Post by achiola on 2009-10-12
> **savagenator said:**
> I found that the temperature will usually stay about those temps. I have a huge heatsink on my AMD, and it still goes over 110 on individual cores.

On my old mobo, my something or other was 69-71 celcius!

Thanks for your replay. I found the problem and fix change the menu.lst:
```
RUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=assign-busses apicmaintimer idle=poll reboot=cold,hard"
```

for
```
RUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=assign-busses apicmaintimer reboot=cold,hard"
```

(remove the idel=poll) 

The complete story [here]("http://www.achiola.com.ar/content/grub-grub2-problemas-de-temperatura-en-mi-nb"). (spanish).

Thanks again and sorry for my english...

---

