---
title: "i7 7500U Kaby Lake HD620 - 16.04 vs 17.04"
date: 2017-09-27
forum: Hardware
---

### Post by frogotronic on 2017-09-27
Hello,

   Getting a new laptop in a couple of days and wondering whether or not to go with 16.04.x LTS or 17.04 flavour of Ubuntu.  It will have the Intel i7 7500U Kaby Lake HD 620 chipset & graphics card.  Is this chipset better supported on 17.04, or is it well supported on 17.04?

Thanks,
Andor

---

### Post by ajgreeny on 2017-09-27
For the system constituents that might affect the support for the new hardware you will probably find that there is no difference between 16.04.3 point release and 17.04, both having the same 17.04 kernel and graphics package versions installed.

Try both as live USBs and see if there is a notable difference; I suspect none will be obvious.

---

### Post by oldfred on 2017-09-27
What brand/model system?
What graphics card/chip?

       Linux Memory Performance With Intel Kabylake From DDR4-1600 To DDR4-3333MHz
[URL="http://www.phoronix.com/scan.php?page=article&item=linux-ddr4-3333&num=1"]http://www.phoronix.com/scan.php?page=article&item=linux-ddr4-3333&num=1
[/URL]
 Issue affecting some Skylake/Kaby Lake processors if hyper-threading enabled.
[https://ubuntuforums.org/showthread.php?t=2364663](https://ubuntuforums.org/showthread.php?t=2364663) 

On my Skylake system with Intel video and 16.04, I did update Intel firmware.

[URL="http://www.phoronix.com/scan.php?page=article&item=linux-ddr4-3333&num=1"]
[/URL]

---

### Post by frogotronic on 2017-09-27
> **oldfred said:**
> What brand/model system?
What graphics card/chip?

       Linux Memory Performance With Intel Kabylake From DDR4-1600 To DDR4-3333MHz
[URL="http://www.phoronix.com/scan.php?page=article&item=linux-ddr4-3333&num=1"]http://www.phoronix.com/scan.php?page=article&item=linux-ddr4-3333&num=1
[/URL]
 Issue affecting some Skylake/Kaby Lake processors if hyper-threading enabled.
[https://ubuntuforums.org/showthread.php?t=2364663](https://ubuntuforums.org/showthread.php?t=2364663) 

On my Skylake system with Intel video and 16.04, I did update Intel firmware.

[URL="http://www.phoronix.com/scan.php?page=article&item=linux-ddr4-3333&num=1"]
[/URL]

System76 Lemur7 (Clevo)
Intel 3.5 GHz i7-7500U (2.7 up to 3.5 – 4 MB Cache – 2 Cores – 4 Threads)
HD620 Graphics
32 GB RAM

---

### Post by frogotronic on 2017-09-27
The Sky Lake and Kaby Lake Intel microcode bug is fixed: [https://bugs.launchpad.net/ubuntu/xenial/+source/intel-microcode/+bug/1700373](https://bugs.launchpad.net/ubuntu/xenial/+source/intel-microcode/+bug/1700373)

---

### Post by mc4man on 2017-09-28
I'd check it out with whatever version you ordered it with. Biggest choice would be if you ordered 17.04 do you want to go with the current Ubuntu direction as 17.04 will be EOL early next year.

---

### Post by frogotronic on 2017-10-03
Yeah, I decided to go with 16.04 for stability and support.  Plus, it's using the HWE kernel anyway.  Thanks

---

