---
title: "clock-rate is not set correctly after cpu upgrade"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by arakes on 2008-01-14
Hi, I installed a new cpu in my Thinkpad R50e (upgrade from Celeron 1,4 GHz to Pentium M 1,86 GHz). However, the clock-rate of the cpu is not correctly identified.
cat /proc/cpuinfo shows the following:
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 13
model name : Intel(R) Pentium(R) M processor 1.86GHz
stepping : 8
cpu MHz : 1400.000
cache size : 2048 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips : 2799.61
clflush size : 64

and
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
shows this:
1400000 1200000 1000000 800000 600000

So the max. clock-rate is 1,4 GHz instead of 1,86 GHz. Has anybody an idea what I could try out to set the max. clock-rate correctly ?

---

### Post by polmir on 2008-01-14
```
sudo update-pciids
```

---

### Post by arakes on 2008-01-14
ok, I tried 
sudo update-pciids
and get the following output:
--23:40:12--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 129,423 (126K) [text/plain]

100%[====================================>] 129,423       81.99K/s             

23:40:14 (81.73 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [129423/129423]

Done.

However, the available cpu-frequencies have not changed.

---

### Post by polmir on 2008-01-14
This is your pc? Yes or no *(this is manual)*
[ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/39t2462.pdf]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/39t2462.pdf")
[ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/c79plac41.pdf]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/c79plac41.pdf")
[ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/39t2400.pdf]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/39t2400.pdf")

To start BIOS Setup Utility.
Change the items about your new CPU.

---

### Post by Yellow Pasque on 2008-01-14
Nothing's wrong with your CPU, it just throttles back to a 6 multipler at idle to save power (6*233 = 1.4GHz) as opposed to running at 8*233=1.86GHz under load.

Edit: Oh, I see. cpufreq didn't change max value. Try:
```
sudo cpufreq-set -u 1860MHz
```

Edit2: You may need to install cpufrequtils if you don't have them.

---

