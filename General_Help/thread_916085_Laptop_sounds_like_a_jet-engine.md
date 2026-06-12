---
title: "Laptop sounds like a jet-engine"
date: 2008-09-10
forum: General Help
---

### Post by del_diablo on 2008-09-10
I recently converted from Win Vista to Ubuntu.
There is 1 thing troubeling me except the other thing(posted in another category), my PC was allmost completely silent when i ran vista on it, there was no noice at all(except when pushing in a CD, the reader is semi-noisy).
So then after a while i start taking notes of how much more sound my laptop makes, it sounds like a freaking jet engine(i bet it could compete with my old PC, big thing.).

PS: running a AMILO Notebook Pa 3553

---

### Post by jigsaws on 2008-09-10
Maybe problem with a cooler?
Check cpu load by top command.

---

### Post by del_diablo on 2008-09-10
> **jigsaws said:**
> Maybe problem with a cooler?
Check cpu load by top command.

i typed top and got this ridiculess diplay up, whattodo?

---

### Post by Tom--d on 2008-09-10
Post the outcome of
```
acpi -t
```

---

### Post by del_diablo on 2008-09-10
```
Battery 1: charged, 100%
     Thermal 1: ok, 64.0 degrees C
     Thermal 2: ok, 64.0 degrees C
```

OK

---

### Post by del_diablo on 2008-09-10
*bump* Heck i need help here, and i posted what was asked.

---

### Post by shae on 2008-09-11
Yup your processor is a tad warm.  (Mine is at 36C while light browsing)  Check to make sure your laptop has CPU throttling enabled.

---

### Post by p_quarles on 2008-09-11
> **shae said:**
> Yup your processor is a tad warm.  (Mine is at 36C while light browsing)  Check to make sure your laptop has CPU throttling enabled.
To do that, take a look at some system monitoring application (the one in Administration if using the default Ubuntu setup), and run the following command in the terminal:
```
cpufreq-info
```
That will output information about how CPU scaling is currently configured.

---

### Post by jigsaws on 2008-09-11
In "top" command check "load", "Idle %" and top processes.
Or simply post here result.

---

### Post by del_diablo on 2008-09-11
```
cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
```

Ok.................... 

On top: 

```

  PID USER      PR  NI  VIRT  RES  SHR S %MEM %CPU    TIME+  COMMAND            
 5769 root      20   0  488m  50m  22m S  1.4    1   0:22.30 Xorg               
 6120 user      20   0  296m  28m  14m S  0.8    1   0:01.76 gnome-panel        
 6713 user      20   0 18860 1260  932 R  0.0    1   0:00.14 top                
    1 root      20   0  4020  880  592 S  0.0    0   0:00.86 init               
    2 root      15  -5     0    0    0 S  0.0    0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0    0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0    0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0    0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S  0.0    0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S  0.0    0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S  0.0    0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S  0.0    0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S  0.0    0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S  0.0    0   0:00.00 khelper            
   44 root      15  -5     0    0    0 S  0.0    0   0:00.00 kblockd/0          
   45 root      15  -5     0    0    0 S  0.0    0   0:00.00 kblockd/1          
   48 root      15  -5     0    0    0 S  0.0    0   0:00.00 kacpid             
   49 root      15  -5     0    0    0 S  0.0    0   0:00.00 kacpi_notify       
  151 root      15  -5     0    0    0 S  0.0    0   0:00.04 kseriod          
```

do not really understand, but ok.

---

### Post by p_quarles on 2008-09-11
Looks like like there is no scaling software running. 

What kind of CPU does this computer have? Most likely with a little tweaking, you should be able to get this working, and that will make the fan noise die down considerably.

---

### Post by del_diablo on 2008-09-11
I found the dam specs for it:

Beskrivelse	Fujitsu Siemens bærbar PC 
AMILPA3553E01 

Bærbar PC fra Fujitsu Siemens med AMD Turion 64 X2 Dual-Core Mobile prosessor. 	 	 	 
Kunderangering	      (6) 	 	 	 
Prosessortype (CPU)	AMD Turion 64 X2 Dual-Core Mobile 	 	 	 
Prosessornummer	RM-70 	 	 	 
Prosessorhastighet i Ghz	2,00 	 	 	 
Minnetype (RAM)	DDR2 	 	 	 
Minnehastighet i MHz	800 	 	 	 
Minne i MB	4 096 	 	 	 
Maksimalt oppgraderbart minne i MB	4 096 	 	 	 
Cache i Kb	1 024 	 	 	 
Lagringskapasitet i GB	320 	 	 	 
Harddiskhastighet i rpm	5 400 	 	 	 
Lydkorttype	7.1 (8 channels) and S/PDIF 	 	 	 
Lydkort i bit	16 	 	 	 
Integrerte høyttalere	 	 	 	 
Integrert Subwoofer	 	 	 	 
Skjermkorttype	ATI Mobility Radeon&#8482; HD 3470 Hybrid X2ATI Radeon&#8482; HD 3200 	 	 	 
Dedikert videominne i MB	256 	 	 	 
Analogt modem	 	 	 	 
Nettverkskort (10/100)	 	 	 	 
Trådløst nettverkskort	 	 	 	 
DVD-brenner	 	 	 	 
CD-ROM hastighet (les)	24x 	 	 	 
DVD-ROM hastighet (les)	8x 	 	 	 
CD-R hastighet (skriv)	24x 	 	 	 
CDRW hastighet (overskriv)	16x 	 	 	 
DVD-R hastighet (skriv)	8x 	 	 	 
DVD-RW hastighet (overskriv)	6x 	 	 	 
DVD+R hastighet (skriv)	8x 	 	 	 
DVD+RW hastighet (overskriv)	8x 	 	 	 
DVD+R DL hastighet (skriv)	4x 	 	 	 
Minnekortavleser	 	 	 	 
Fjernkontroll	 	 	 	 
Skjermtype	TFT 	 	 	 
Skjermstørrelse i tommer	15,40 	 	 	 
Maks. skjermoppløsning	1280 x 800 	 	 	 
Standard	WXGA 	 	 
Web-kamera	Innebygd	 	 	 	  	 	 	 
Type TV-utgang	HDMI 	 	 	  	 	 	 
PCMCIA (antall)	1 	 	 	 
PCMCIA (type)	Express Card (34/54 mm) 	 	 	 
USB 2.0 (antall)	3 	 	 	 
FireWire (IEEE 1394)	1 	 	 	  	 	 	 	 
Batteritype	Li-ion 	 	 	 
Pekeutstyr	Touch Pad 	 	 	 
Høyde i cm	3,75 	 	 	 
Bredde i cm	35,80 	 	 	 
Dybde i cm	25,90 	 	 	 
Vekt i kg	2,95

Sorry for posting it in Norwegian, but it was the only readable specs i could find and rip.

---

### Post by p_quarles on 2008-09-12
Okay, please try the following, and post back any error messages you get at any step:
```
sudo apt-get install powernowd
```
If it says it's already installed, go ahead and run:
```
sudo /etc/init.d/powernowd start
```
Finally, try:
```
sudo /etc/init.d/cpufrequtils start
```

---

