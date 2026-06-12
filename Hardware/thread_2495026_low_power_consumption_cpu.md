---
title: "low power consumption cpu?"
date: 2024-02-04
forum: Hardware
---

### Post by josephchrzempiec on 2024-02-04
Hello, Maybe someone can help me out with this. I'm working on a solar powered sever that total power consumption of 50 to 60 watts. I can not find a cpu that is low enough for 35 watts or lower. There are 4 fans that puts out 10 watts total. and there are two 2.5 inch drive that are 1 amp at 5v makes for 10 watts. I only have  35 to 40 watts left for the cpu, motherboard and memory. Does anyone know of an intel processor that is 20 to 30 watts? at least 2 cores 4 threads or 4 cores 4 threads. I don't need much speed.

Edit: I would love to run a low powered ubuntu solar server. I just can not find a good low power cpu.

Joseph

---

### Post by Holger_Gehrke on 2024-02-04
Is there a reason it has to be x86 ? My Raspberry Pi 4 runs of a USB-C power supply rated for 15.3 W. It probably can run with less if wlan and bluetooth are inactive.

Holger

---

### Post by josephchrzempiec on 2024-02-04
That is true. However The only pi I got are pi 3. I would need usb storage then I would have to rig something up to be in a case to put on my server rack. I have pretty much everything besides the cpu and motherboard.


> **Holger_Gehrke said:**
> Is there a reason it has to be x86 ? My Raspberry Pi 4 runs of a USB-C power supply rated for 15.3 W. It probably can run with less if wlan and bluetooth are inactive.

Holger

---

### Post by josephchrzempiec on 2024-02-04
I did manage to find a quad core cpu that has low power [https://www.intel.com/content/www/us/en/products/sku/197305/intel-celeron-processor-j4125-4m-cache-up-to-2-70-ghz/specifications.html](https://www.intel.com/content/www/us/en/products/sku/197305/intel-celeron-processor-j4125-4m-cache-up-to-2-70-ghz/specifications.html)

---

### Post by Doug S on 2024-02-05
Intel Processor power consumption is not linear with CPU frequency. By limiting the maximum CPU frequency the maximum power consumed by the processor can be greatly reduced. My Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz will consume about 115 watts with everything going flat out at 4.8 GHz, but the same work will consume less than 10 watts if the CPU frequency is limited to 0.8 GHz. Obviously the work just takes longer to complete.

My test server is doing a long test at the moment, but I can get you some exact numbers eventually.

EDIT: Add an example:

```
doug@s19:/media/nvme/home/doug/24.04$ sudo /media/nvme/home/doug/kernel/linux/tools/power/x86/turbostat/turbostat --quiet --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 15
[sudo] password for doug:
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
99.76   4800    45488   73      112.80  112.14  0.00    1.33
99.76   4800    45606   73      112.87  112.21  0.00    1.33
99.76   [COLOR="#FF0000"]4800[/COLOR]    45594   74      [COLOR="#FF0000"]113.35[/COLOR]  [COLOR="#FF0000"]112.69[/COLOR]  0.00    1.33
99.76   3208    45299   45      70.54   69.89   0.00    1.33
99.76   800     45655   44      5.75    5.09    0.00    1.33
99.76   800     45545   44      5.88    5.23    0.00    1.33
99.76   [COLOR="#FF0000"]800[/COLOR]     45245   43     [COLOR="#FF0000"] 5.85[/COLOR]    [COLOR="#FF0000"]5.19[/COLOR]    0.00    1.33
99.76   800     45541   43      5.62    4.97    0.00    1.33
99.76   800     45677   44      5.79    5.13    0.00    1.33
```

---

### Post by him610 on 2024-02-06
> Does anyone know of an intel processor that is 20 to 30 watts? at least 2 cores
If you can find one, Intel Atom 330: TDP 8 watts, 2 cores
[https://ark.intel.com/content/www/us/en/ark/products/35641/intel-atom-processor-330-1m-cache-1-60-ghz-533-mhz-fsb.html]("https://ark.intel.com/content/www/us/en/ark/products/35641/intel-atom-processor-330-1m-cache-1-60-ghz-533-mhz-fsb.html")

---

### Post by grimitz on 2024-02-13
Hi Doug, any chance you have those mesurements ready? Just looking on a deal for a 10600 on h470 board that could become my next server

---

### Post by Doug S on 2024-02-14
> **grimitz said:**
> Hi Doug, any chance you have those measurements ready? Just looking on a deal for a 10600 on h470 board that could become my next server I edited my earlier post a week ago with some actual turbostat data. I am not sure what else you want. I do have wall power, but it could not be representative because I have more memory, HDDs, SDDs, and 2 NVMEs.

---

