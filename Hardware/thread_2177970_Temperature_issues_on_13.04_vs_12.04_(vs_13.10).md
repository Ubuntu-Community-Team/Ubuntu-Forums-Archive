---
title: "Temperature issues on 13.04 vs 12.04 (vs 13.10?)"
date: 2013-10-01
forum: Hardware
---

### Post by arnold_layne2 on 2013-10-01
I'm on an HP DV6 6121tx which has switchable graphics AMD HD6770M and Intel integrated. 

First thing I do after installing Ubuntu is ```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
``` to switch off my discrete card, since I don't really need it.Ar


Now my observation is that 12.04 ran much cooler than 13.04 with the discrete card off. Has anyone else noticed that? I can't give you exact numbers on temperatures, but it feels a good 5-10oC higher. 

So I have a few questions.

1. Any fixes to the heat issue? Remember, my discrete card is OFF!
2. Is it wise to switch back to 12.04? 
3. Are LTS versions known to have better hardware compatibility?
4. I've heard 13.10's kernel has a much improved system for managing hardware temperatures. Is it true?


Thanks a lot!

---

### Post by Yellow Pasque on 2013-10-01
> **arnold_layne2 said:**
> 1. Any fixes to the heat issue? Remember, my discrete card is OFF!
2. Is it wise to switch back to 12.04? 
3. Are LTS versions known to have better hardware compatibility?
4. I've heard 13.10's kernel has a much improved system for managing hardware temperatures. Is it true?

1. It depends on what's generating the heat
2. I wouldn't, but I value running updated software
3. No, because they use older kernel, drivers, etc.
4. I heard the Queen of England is really an alien! Seriously though, you're probably referring to the new radeon dynamic power management code, which doesn't help if your radeon card is off: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

