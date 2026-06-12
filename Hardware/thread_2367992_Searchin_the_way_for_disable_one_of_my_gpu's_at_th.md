---
title: "Searchin the way for disable one of my gpu's at the moment of installing..."
date: 2017-08-05
forum: Hardware
---

### Post by erikebz on 2017-08-05
So yep, i have an HP pavilion ab010la with the next HW:

17.7.2
Crimson ReLive
AMD Radeon R6 Graphics  (512 MB) as integrated gpu
AMD Radeon R7 M360 as secondary gpu with 2 GB 
DDR3
Windows 10 (64 bit)
12 GB
AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G
[http://i.imgur.com/DFnYIpw.png](http://i.imgur.com/DFnYIpw.png) those are the especifications but they are in spanish :s

what i want to do is disable the AMD Radeon R7 M360 for just use the R6 Graphics with Ubuntu but why?
because my laptop is fully of problem tying to install ubuntu with the 2 gpus...


i found this video [https://www.youtube.com/watch?v=PVJyrCFtFeE](https://www.youtube.com/watch?v=PVJyrCFtFeE) but i dont know how to do this process before the installing alongside whit W10 :s

---

### Post by TheFu on 2017-08-06
To disable on-board hardware, do it in the BIOS.  There is always a setting for this stuff - like enable/disable the onboard SATA or serial or USB or network adapters are all settings in the BIOS.

Some low-end hardware limits the BIOS controls and HP is especially fond of removing those screens.  Some HP models have all the settings and others have only a small part of the BIOS controls.  It just depends.

---

### Post by erikebz on 2017-08-06
then it is not possible :c?

---

### Post by SeijiSensei on 2017-08-06
Is it a separate adapter card?  If so, you can just remove it from the system before installation.

---

### Post by QIII on 2017-08-06
> **erikebz said:**
> then it is not possible :c?

As TheFu suggested, please check to see if your BIOS allows you to disable one or the other of the adapters.  It is not likely that you will be able to remove the dedicated adapter from a laptop.  It is probably "soldered-in".

We are in a bit of unfamiliar territory right now with AMDGPU and AMDGPU-PRO.  I haven't seen documentation on switchable graphics in laptops and I no longer have a suitable laptop to experiment on myself.  However, I do know that your AMD A10-8700P APU (Carrizo series) is fully supported by AMDGPU.   If you can disable the dedicated graphics adapter, you should be able to use the APU's on-die GPU.

---

### Post by erikebz on 2017-08-06
Well i checked the bios and yep it does not have the option to disable the gpus, and as u say the gpus are solidered and i cant just take them out of the laptop...

I found a video wich explain a method but idk if it si safe to do, actually i find a way to install linux using the "nomodeset" and then run it but when i restar the pc it never runs and just stay in a black screen.

I can run ubuntu with an USB in live mode...

Well im thinking about installing another flavor of linux but i heard that ubuntu is the best...

---

