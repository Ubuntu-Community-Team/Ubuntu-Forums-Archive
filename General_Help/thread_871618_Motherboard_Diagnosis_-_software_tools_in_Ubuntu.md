---
title: "Motherboard Diagnosis - software tools in Ubuntu?"
date: 2008-07-27
forum: General Help
---

### Post by darkworld on 2008-07-27
Is there software in ubuntu or command line methods for tracing possible hardware faults? I think something is wrong with my motherboard but dont know how I can track exactly what it is.

It started by not restarting, Ubuntu system boots down and just sits there, does the same from XP. Then days later it started freezing before it got to Grub menu. Couple of reboots would get it back going. 

Went on holiday for a week, booted machine on return and it froze earlier in POST.

How can I trace whats wrong? Ubuntu tools or command line????

Any help much appreciated.

---

### Post by dexter.deepak on 2008-07-27
i think lm-sensors can help you.

---

### Post by pooyaplus on 2008-07-27
Hi, does you motherboard support S.M.A.R.T ?

---

### Post by darkworld on 2008-07-27
I cant get Im sensors to work at the moment but currently trying. I took a look in Bios and voltages etc are right, fans etc right.

Im not sure what smart is but will look up. Its a newish board MBB-AM462M MOBO BUN AMD X2 4600 2GB RAM bought 6 months ago. Will SMART be listed in BIOS somewhere?

---

### Post by dexter.deepak on 2008-07-27
> **darkworld said:**
>  Will SMART be listed in BIOS somewhere?

yes it would be.

---

### Post by darkworld on 2008-07-27
> k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +44.0°C                                    
Core1 Temp:  +48.0°C                                    

it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.09 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +1.23 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.30 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +4.95 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +11.90 V  (min =  +0.00 V, max = +16.32 V)
-12V:        -2.45 V  (min = -27.36 V, max =  +3.93 V)
-5V:         -5.46 V  (min = -13.64 V, max =  +4.03 V)
Stdby:       +4.97 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.02 V
fan1:       2766 RPM  (min =    0 RPM, div = 2)
fan2:          0 RPM  (min =    0 RPM, div = 2)
fan3:       7758 RPM  (min =    0 RPM, div = 2)
M/B Temp:    +42.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
CPU Temp:    +38.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = transistor
Temp3:       +21.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = transistor
cpu0_vid:   +1.100 V

 The -12V shows -2.45 V ??????

Ive looked in Bios Winfast Smart Bios BIOS ID 6150M2MA.01.WI.P.17

Only reference to smart was Smart boot menu, which I enabled and that just lets me select drives at boot pre grub. I also noticed it said Smart LED - debug through power led.

Lastly I found the fault also occurs coming out of BIOS. Exit BIOS and pc drops screen, goes black and screen led in stanby, PC fan running but nothing happening and no PC power light even though its running, just not attempting to go to boot.

Ive tried to see what happens during shutdown by alt+f1 but it only shows me so far before it skips back to graphical shutdown. Can I get a verbose output of total shutdown restart?

---

### Post by pooyaplus on 2008-07-27
> **darkworld said:**
> Im not sure what smart is but will look up. Its a newish board MBB-AM462M MOBO BUN AMD X2 4600 2GB RAM bought 6 months ago. Will SMART be listed in BIOS somewhere?

Yes it must be listed, and when booting up, it should say that if it is enabled or not.

---

### Post by darkworld on 2008-07-27
only smart boot - enabled that - cant find anything else smart in the various BIOS pages. What will this do for me if its there? 

on the LM sensor issue -12V = -2V  is this a red herring?

---

### Post by knutschr on 2008-07-27
```
sudo apt-get install smartmontools
```

---

### Post by pooyaplus on 2008-07-27
SMART will notify you of the possible problems with your hard disk and your motherboard. 

[http://en.wikipedia.org/wiki/Self-Monitoring%2C_Analysis%2C_and_Reporting_Technology]("http://en.wikipedia.org/wiki/Self-Monitoring%2C_Analysis%2C_and_Reporting_Technology")

---

### Post by darkworld on 2008-08-05
Thanks for all the above. Ive run the smart tools and I dont appear to have any disk problems. I contacted Novatech technical and so far the only suggestion they have is to change the power supply. ????

Is this likely to stop a reboot???

---

### Post by pooyaplus on 2008-08-05
I guess so.You can give it a try.
good luck

---

### Post by cariboo on 2008-08-05
I would suggest a power supply also, If you are getting strange voltages when running sensors. If your tech support is suggesting a power supply, get them to send you a new one, a it should still be under warranty.

Jim

---

