---
title: "Does 7.04 fix laptop overheating?"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by WsfWarlord on 2007-04-20
or do i have to search for another linux to install? ^^

when i tried to install the previous ubuntu release i had that overheating error (going to 104°) with a shutdown, searching around about that problem didn't help me at all so i was thinking about trying another linux, and then i see a new ubuntu is out, so.... it's downloading right now, but before i risk burning off my laptop i'd like to know ^^

i also tried running USBuntu but that one would crash while launching, not sure yet if it's because it's not properly installed on my USB drive or if it's related to that overheating problem..

and before you ask, it's an acer aspire 1520,  there's no dust blocking the fan, i even changed thermal paste since i had the feeling that there wasn't enough of it, and windows can run games like need for speed most wanted without overheating.

---

### Post by WsfWarlord on 2007-04-21
i guess i'll have to try myself then...

---

### Post by kevinatkins on 2007-04-21
Hi,

I had an overheating issue with Edgy - laptop would overheat and shut off. I ended up going back to Dapper which was OK. I've installed Feisty on the same machine and it seems absolutely fine - no problem.

FYI it's a Celeron 2GHz machine - it's essentially a desktop chipset with a desktop processor, so it does generate quite a bit of heat. I believe a number of P4 laptops also use a desktop processor and also tend to run warm.

I also recently cleaned out a lot of fluff from the CPU heatsink, which stopped the fan from screaming away trying to keep the thing cool - worth checking.

In short, Feisty / 7.04 seems fine with my laptop!

---

### Post by kingkookie on 2007-04-23
My laptop (HP Pavilion ze4547wm) runs hot to the touch with Dapper, Edgy, and Feisty.    Not just the CPU was hot, the entire laptop was hot.  In fact, I had a 512mb DIMM that went bad while running Edgy, and it's quite likely that it was caused by overheating.  It's not very common for a DIMM to just suddenly go bad.

This issue is one of the critical known bugs, which, as far as I know, is still unresolved.

---

### Post by psiu on 2007-04-23
Mine hasn't appeared to overheat yet--a P3 1.2Ghz usually idles at around 60-65 maybe 70 in Windows. Haven't found temp monitoring in Ubuntu yet but it hasn't gone critical and shutdown, at the very least.

---

### Post by Ranbaz on 2007-04-24
> **WsfWarlord said:**
> or do i have to search for another linux to install? ^^

when i tried to install the previous ubuntu release i had that overheating error (going to 104°) with a shutdown, searching around about that problem didn't help me at all so i was thinking about trying another linux, and then i see a new ubuntu is out, so.... it's downloading right now, but before i risk burning off my laptop i'd like to know ^^...
I only use Ubuntu on my Toshiba Satellite pro 6050 (upgraded with a PIII 1.2Ghz). I had the same overheating problem when I tried "Edgy" and now with "Feisty". I want to go back once again with Dapper but I can't easily backup my "Home" folder because the laptop freezes during the copy ...:( :( :( I will try file by file...pfff

---

### Post by Ranbaz on 2007-04-24
> **psiu said:**
> Mine hasn't appeared to overheat yet--a P3 1.2Ghz usually idles at around 60-65 maybe 70 in Windows. Haven't found temp monitoring in Ubuntu yet but it hasn't gone critical and shutdown, at the very least.

Use this to see your laptop temp. ```
cat /proc/acpi/thermal_zone/THRM/temperature
```  or for more information ```
cat /proc/acpi/thermal_zone/*/*
```

---

### Post by Jeffj on 2007-05-15
> **Ranbaz said:**
> Use this to see your laptop temp. ```
cat /proc/acpi/thermal_zone/THRM/temperature
```  or for more information ```
cat /proc/acpi/thermal_zone/*/*
```

I tried installing every temperature utility I could see in the synaptic package monitor but I haven't been able to try them all. There is nothing in my thermal_zone directory.

I have a gateway 7510GX. It has always been a little warm running Ubuntu but it seems extra warm now. I should probably disassemble and clean but it doesn't get this hot in Windows.

---

