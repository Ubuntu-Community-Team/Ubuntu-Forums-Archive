---
title: "processor speed problem"
date: 2009-01-30
forum: Hardware
---

### Post by teodormitev on 2009-01-30
hi.i have install ubuntu 8.10 on my LENOVO n200 with T5850 processor(2,18Ghz).When i start conky program i see that my cpu is working on 1000 Mhz.The notebook is on AC.Where might be the problem.
Thx

---

### Post by zika on 2009-01-30
> **teodormitev said:**
> hi.i have install ubuntu 8.10 on my LENOVO n200 with T5850 processor(2,18Ghz).When i start conky program i see that my cpu is working on 1000 Mhz.The notebook is on AC.Where might be the problem.
Thx
that is CPU freq. scaling working for You. in case You fire up app. that needs CPU it will increase its speed to max. (powernowd) You can turn that off in System -> Admin. -> Services.

---

### Post by teodormitev on 2009-01-30
can i make the cpu working at max speed when is on ac an scaling the frequency when it use battery

---

### Post by bruce89 on 2009-01-30
> **teodormitev said:**
> can i make the cpu working at max speed when is on ac an scaling the frequency when it use battery

You can, but it's pointless and only wastes electricity.

---

### Post by Tubes6al4v on 2009-01-30
I find that my hard drive is usually the culprit for lag. That's why it is nice to have lots of RAM, so you only need to access it once from the HD.

---

### Post by teodormitev on 2009-01-30
i'v typed the command  cat /proc/cpuinfo in terminal and that is the result

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4322.47
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4322.49
clflush size	: 64

```

cpu MHz		: 1000.000
is that current cpu speed?

---

### Post by Ben Page on 2009-01-30
yes, that is current CPU speed. Add to panel a gadget called cpu scaling (right click on panel and chose from list). The you can left click on the gadget and you will get a list of modes, choose performance to keep your CPU at max at all time.
Check out this thread, it has some info on CPU scailing> [http://ubuntuforums.org/showthread.php?t=1051456&highlight=processor+frequency%3F](http://ubuntuforums.org/showthread.php?t=1051456&highlight=processor+frequency%3F)

---

### Post by Francewhoa on 2009-01-31
Same here with Ubuntu 8.04 and Toshiba A8 laptop. The following worked for me.

CPU frequency manager has been integrated into Ubuntu 8.04 power management UI but is disabled by default.

To enable it, open *Terminal* via menu *Application > Accessories > Terminal*

run: ```
gconf-editor
```The* 'Configurator Editor - ui'* window will open.

Navigate to folders *apps > gnome-power-manager > ui*
    
Under *VALUE* column check *'cpufreq_show'*

Close the The* 'Configurator Editor - ui'* window.

Now if you access *'Power Management'* through System > *Preferences* menu or the applet right-click menu you have the following options under* 'Actions'* >* 'Computer speed policy'* on AC and battery power: *Always maximum speed, Based on processor load and Maximum power saving.* With last setting* 'Maximum power saving'* battery last longer & fan is quieter.

Enjoy

---

### Post by TMachado on 2009-03-15
> **Onopoc said:**
> Same here with Ubuntu 8.04 and Toshiba A8 laptop. The following worked for me.

CPU frequency manager has been integrated into Ubuntu 8.04 power management UI but is disabled by default.

To enable it, open *Terminal* via menu *Application > Accessories > Terminal*

run: ```
gconf-editor
```The* 'Configurator Editor - ui'* window will open.

Navigate to folders *apps > gnome-power-manager > ui*
    
Under *VALUE* column check *'cpufreq_show'*

Close the The* 'Configurator Editor - ui'* window.

Now if you access *'Power Management'* through System > *Preferences* menu or the applet right-click menu you have the following options under* 'Actions'* >* 'Computer speed policy'* on AC and battery power: *Always maximum speed, Based on processor load and Maximum power saving.* With last setting* 'Maximum power saving'* battery last longer & fan is quieter.

Enjoy

I have the information when I start ubuntu 8.10, that scalling is not supported. In the past, I could (with the same computer) change profiles, but now I cant do it since I reinstalled ubuntu.

In 'UI', I do not have column cpu freq show.

By now I have cpufreqd installed, and powernowd not installed. Can anyone please help me?

---

