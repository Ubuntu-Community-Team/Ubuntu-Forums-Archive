---
title: "Earphone mute switch doesn't work with my custom Kernel on my Dell Inspiron 6400"
date: 2009-04-29
forum: Hardware
---

### Post by gana.ssa on 2009-04-29
Hi
I have a Dell Inspiron 6400 with a Ubuntu 8.10.
After a Kernel customization & recompile, I've lost the auto-mute switching when plugging in a jack in the earphone.
With the standard Kernel this switch is working correctly.

Here is my Kernel version:

```
$ uname -a
Linux gray 2.6.27.2-inspiron6400-bestfit-v3 #1 PREEMPT Sun Apr 26 03:34:14 CEST 2009 x86_64 GNU/Linux
```

Here is how Ubuntu configured (correctly) the alsa module related:

```
$ sudo cat /etc/modprobe.d/alsa-base |grep snd-hda-intel
options snd-hda-intel model=dell-m21
```

and this is the diff to an lsmod text files obtained with my custom kernel ("<" left side") and another lsmod output text file from the standard kernel (">" right side).
I think the missing part should be one of the modules missing on my kernel listed on the right side of this diff, but I can't understand which one:

```
diff lsmod_bestfit_ordered_cut.txt lsmod_standard_ordered_cut.txt
14a15
> container           
15a17
> cpufreq_ondemand    
17a20
> cpufreq_userspace   
22d24
< drm                 
29a32
> freq_table          
31d33
< i915                
36a39,41
> ipv6                
> iTCO_vendor_support 
> iTCO_wdt            
37a43
> joydev              
39a46
> lp                  
46a54,56
> parport             
> parport_pc          
> pata_acpi           
53d62
< ricoh_mmc           
87a97
> wmi                 
```

Anyone can help me?

In case you're interested, I'll attach the config file of my custom kernel (very optimized):

---

### Post by gana.ssa on 2009-04-30
Up

---

