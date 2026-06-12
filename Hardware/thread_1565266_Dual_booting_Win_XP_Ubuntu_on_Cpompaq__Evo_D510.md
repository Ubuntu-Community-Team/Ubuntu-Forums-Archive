---
title: "Dual booting Win XP /Ubuntu on Cpompaq  Evo D510"
date: 2010-08-31
forum: Hardware
---

### Post by AVHATION on 2010-08-31
After a pathetically long time I have achieved the above so I thought I should share the information. I was constrained by having only a basic legit CD for Win XP Pro and SP1a which I could get to run without internet connection, audio, or  USB,  However, loading a downloaded copy of the SP2 upgrade made the screen resolution so low as to be almost unusable and did not solve the other driver issues.  Also, it turned out that the "new to me" Compaq computer was an ex-business machine which was no longer supported by Compaq. 
To cut a long and tedious story short, I used Ubuntu to find out the make and model of the motherboard, which led me to Intel where I found a selection of drivers which I copied onto a CD using Ubuntu. When I reloaded these drivers for all the hardware which Win XP had reported as having problems, everything came good.  Clues for other users of this machine type:
Display graphics accelerator = Intel Win2K-XP 14103.zip (not the optional Nvidia 25192)
USB =  ???210 – (or USB 2.0.exe)
Audio = Intel 27103
Chipset controller = Intel 27532.
Network adapter = PRO Win32

The only residual problem is Ubuntu crashing which I think might be connected to screensaver settings - certainly changing settings will bring it on. 

Thanks to all who have recorded their experiences. I hope this will help others who like me depend on this forum!

---

