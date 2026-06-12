---
title: "my cpu seems slow"
date: 2010-05-06
forum: Hardware
---

### Post by tropdoug on 2010-05-06
I have a dual core AMD processor (See attachment 1) that should fly my system, however I am suffering lots of slow downs as programs work. 

I did some research on the CPU and found that it should be running at 2800 Mhz (I think) 

I am not to technical in this area. Can anyone tell me if the info in the attachments indicates the CPU is running slow? or if I should look elsewhere please.

---

### Post by sxmaxchine on 2010-05-06
what kernel version do have installed these commands might be helpful
To check kernel version:
->uname -v
To check kernel release:
->uname -r
To check kernel name:
->uname -s

---

### Post by sxmaxchine on 2010-05-06
you might also try this command to get information about your cpu using the terminal, use this code:
cat /proc/cpuinfo

---

### Post by tropdoug on 2010-05-06
If I am reading this right, then each core is running at 800 Mhz, so even combined is way down from 2800? 

douglas@desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) X2 240 Processor
stepping    : 2
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 5624.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) X2 240 Processor
stepping    : 2
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 5625.54
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

douglas@desktop:~$

---

### Post by tropdoug on 2010-05-06
I get this 

douglas@desktop:~$ uname -vrs
Linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010

---

### Post by sxmaxchine on 2010-05-06
you might need to update your kernel if you are using lucid you can use these instructions might work on 9.10 and 9.04.

[here are the files]("http://kernel.ubuntu.com/~kernel-ppa....6.33.3-lucid/")

if you have 64bit
sudo dpkg -i linux-image-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb
sudo dpkg -i linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb
sudo dpkg -i linux-headers-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb

and for 32 bit
sudo dpkg -i linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
sudo dpkg -i linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb
sudo dpkg -i linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb

i hope this helps fix your problem

---

### Post by tropdoug on 2010-05-08
When I ran the dpkg command I got the following

sudo dpkg -i linux-image-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb
[sudo] password for douglas: 
dpkg: error processing linux-image-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb

I downloaded the latest 64bit torrent last night and installed it today, then ran the above command, so I am presuming that 2.6.32 is in fact the latest image available?

---

### Post by tropdoug on 2010-05-08
This is the result of cat/proc/cpuinfo on the new install of lucid 64bit. (the previous one was a 32bit install) 

Processor 0 is still at 800 Mhz but processor 1 is now at its correct 2800 Mhz, does anyone know if this is correct now, or if I should be able to get bothe processors ruinning at 2800?

douglas@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) X2 240 Processor
stepping    : 2
[COLOR=Blue]**cpu MHz        : 800.000**[/COLOR]
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 5625.45
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) X2 240 Processor
stepping    : 2
[COLOR=Blue]**cpu MHz        : 2800.000**[/COLOR]
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 5625.63
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

douglas@ubuntu:~$

---

### Post by dtfinch on 2010-05-08
The bogomips looks correct (about double the clock rate). You might be seeing the effects of AMD Cool'n'Quiet downclocking the core when idle.

---

### Post by tropdoug on 2010-05-08
I found some more info at 

[http://ubuntuforums.org/showthread.php?t=1269470](http://ubuntuforums.org/showthread.php?t=1269470) 

It appears others have the same issue. Can anyone tell me what dmidecode and the m3 after the grep means

because when I did this using dmidecode | grep m1 ¨current Speed"it returned 2800 Mhz. Now because I have two processors running, I thought maybe the 1 related to the first processor, so I tried m2 and got two lines of info amd then m3 gives me three lines of info. m4 does not give four lines. So now I ask myself what does the whole command actually mean, and what are the 32 ns and 144 ns figures (I am thinking ns stands for nano second?)

[CODE][sudo dmidecode | grep -m3 "Current Speed"
    Current Speed: 2800 MHz
    Current Speed: 32 ns
    Current Speed: 144 ns
/CODE]

I have also found out, apparently that cat/proc/cpuinfo does not give you the actual current running speed of your cpu. Not sure if that is correct, but that is stated in a number of threads.

Any more ideas anyone?

---

### Post by tropdoug on 2010-05-08
Thanks dtfinch -- umm what are bogomips?

---

