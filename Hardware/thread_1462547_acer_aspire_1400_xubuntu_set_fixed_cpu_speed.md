---
title: "acer aspire 1400 xubuntu set fixed cpu speed ?"
date: 2010-04-25
forum: Hardware
---

### Post by mistamcgoo on 2010-04-25
i reinstalled my acer aspire1400 from kubuntu 6.10 to xubuntu 9.10.

With kubuntu, i had a little program in the taskbar that let me set the "cpu governors" and worked great always. 
The problem with this laptop is that the processor has bad cooling, making it run its fans quite loudly all the time.
with ktemperature, i set it to "powersave", that kept my laptop at 500 mhz or so and good temperatures

now i tried everything i could find on the xfce synaptic installer, but i can't find any program that actually succeeds in setting a low cpu speed. i tried both powernowd and cpufreqd, looked trough the man pages for correct usage, but nothing actually happens when i try all the different commands

for cpufreqd, i read that the conservative and powersave profiles are disabled? that makes it useless to me then.

xfce-cpufreq plugin on the taskbar keeps showing it at 1200 mhz, and so does cat /proc/cpuinfo 
the other taskbar plugin that lets you change the governors seems to recognize all the scaling steps in my cpu and all, but nothing actually changes, and the fan keeps spinning terribly.

anyone any ideas?

---

### Post by Yellow Pasque on 2010-04-25
```
sudo apt-get install cpufrequtils
sudo cpufreq-set -g conservative
```

---

### Post by mistamcgoo on 2010-04-25
i really don't know what i'm doing wrong here, but it doesn't seem to work, i succesfully installed the cpufrequtils, and i tried that command and a few others i found in the man page, but the frequency stays stuck for some reason. the commands don't return any errors. 

i have powernowd also installed (don't know if this matters)

in the xfce cput frequency monitor taskbar plugin, it does show 
all the available frequencies (500 mhz-1.2 ghz) and all 5 governors. 
after scaling driver it says "powernow-k7". 

could this make anyone any wiser?

EDIT : i noticed that with the 
sudo cpufreq-set -g conservative
command the actual governor does change, as it appears in the taskbar icon, but the cpu speed remains stuck. is there any configuration file i need to set the cpu speeds per governor or so? 
sudo cpufreq-set -f 500 MHz doesn't help either

---

### Post by Defrector on 2010-06-24
consider:
```

sudo cpufreq-set -g ondemand
sudo cpufreq-set --min 500MHz --max 500MHz

```

I had a similar issue which this workaround appears to address; perhaps it will address your issue as well.

---

### Post by ingeniera on 2011-01-15
**** help this newbie girl ***** !!

I have exactly the same problems...
I can't even find this  xfce cput frequency monitor taskbar plugin, although I just installed power manager for the Xfce panel plugin.
I also used this command
sudo cpufreq-set --min 500MHz --max 500MHz

and got the message


Error setting new values. Common errors:
- Do you have proper administration rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set an invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   or because the userspace governor isn't loaded?


Any ideas?
I had ubuntu and the fan worked great but it was heavy for my old laptop so put xubuntu instead. It is more lightweight, still it is very noisy (not as much as my windows installation though).

---

### Post by ingeniera on 2011-01-15
Amilo-M1450-Series:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.60GHz
stepping	: 8
cpu MHz		: 1600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips	: 3200.71
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:


As you can see there is no power management..

---

