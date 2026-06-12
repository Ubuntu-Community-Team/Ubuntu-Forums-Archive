---
title: "Overclocking"
date: 2012-05-14
forum: Hardware
---

### Post by Jerry421 on 2012-05-14
Hello I am trying to overclock my cpu so i can use it as my main OS for my laptop I found this program k10ctl [http://www.ztex.de/misc/k10ctl.e.html](http://www.ztex.de/misc/k10ctl.e.html)  I was wondering if someone could tell me step by step on how to install it. I seem to be having problems lol

---

### Post by matt_symes on 2012-05-14
Hi

I may be able to help you. I do not have the same processor but...


Also if you break your machine then don't blame me.


First things first, download the tar.bz2 file.


Open a terminal and type


```
cd && wget http://www.ztex.de/misc/k10ctl.tar.bz2
```
You then need to extract it from the archive


```
tar -xvf k10ctl.tar.bz2
```
Change to the directory


```
cd k10ctl
```
There are a couple of prerequisites to running the module. You need the msr device nodes present under /dev. To do this you load the msr kernel module.


```
sudo modprobe msr
```
Check you can see the nodes with (and have read write access)


```
ls -l /dev/cpu/*/msr
```
Check you can see (and have read access to)


```
ls -l /proc/bus/pci/00/18.3
```
Now read the readme and other files in the folder.


You will need to run the k10ctl commands with elevated privilages do use sudo. ie


```
sudo k10ctl ......
```
This will not persist over reboots. To do that you will need to add something to a startup script.


Post back on how you get on.


Kind regards

---

### Post by Jerry421 on 2012-05-14
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ ls -l /dev/cpu/*/msr
crw------- 1 root root 202, 0 May 14 21:39 /dev/cpu/0/msr
crw------- 1 root root 202, 1 May 14 21:39 /dev/cpu/1/msr
crw------- 1 root root 202, 2 May 14 21:39 /dev/cpu/2/msr
crw------- 1 root root 202, 3 May 14 21:39 /dev/cpu/3/msr
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ ls -l /proc/bus/pci/00/18.3
-rw-r--r-- 1 root root 4096 May 14 21:40 /proc/bus/pci/00/18.3
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ sudo k10ctl
sudo: k10ctl: command not found
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ k10ctl <cpu>
bash: syntax error near unexpected token `newline'
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ k10ctl <cpu>[-<cpun>]
bash: cpu: No such file or directory
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ sudo k10ctl -h
sudo: k10ctl: command not found
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ sudo k10ctl
sudo: k10ctl: command not found

---

### Post by matt_symes on 2012-05-14
Hi

> jerry@jerry-HP-Pavilion-dv6-Notebook-PC**:~/k10ctl$** sudo k10ctl
sudo: k10ctl: command not found
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:**~/k10ctl$** k10ctl <cpu>
bash: syntax error near unexpected token `newline'
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:**~/k10ctl$** k10ctl <cpu>[-<cpun>]
bash: cpu: No such file or directory
jerry@jerry-HP-Pavilion-dv6-Notebook-PC**:~/k10ctl**$ sudo k10ctl -h
sudo: k10ctl: command not found
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:**~/k10ctl$** sudo k10ctl
sudo: k10ctl: command not found
Hmm. If you in the same directory as an exectuable you want to run ( ^^^^^) then you have to prepend with ./


i.e.


```
sudo ./k10ctl -h
```
If you are in a different directory then


```
sudo /path/to/dir/k10ctl -h
```
If you did not know that then can i advise you to be very careful when you play around with k10ctl.


Kind regards

---

### Post by MartyBuntu on 2012-05-14
> **Jerry421 said:**
> ...overclock my cpu...


...laptop...


Stop.

Save yourself some time and grief.
Minimal gain with MAXIMUM downside (overheating...lower battery life...)

---

### Post by Jerry421 on 2012-05-14
This may be true, but on Windows 7 I used K10Stat and overclocked to 2.6-2.8ghz which it would cycle through to game. which compared to stock would give me about 10 fps more. I can overclock to 2.6 with 1.1125 volts which made the temp go up +2-4 degrees in windows so it wont damage the system that much but without the overclock my laptop is useless with games.

---

### Post by matt_symes on 2012-05-18
Hi

@Jerry421.

I was interested; how you are getting on with the overclocking ?

Kind regards

---

### Post by Jerry421 on 2012-05-20
Hello, Sorry I have been busy the past few days but anyways this is the result of trying the command
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~/k10ctl$ sudo ./k10ctl 0-3 1 -cv 30 -cf 6
Warning: No AMD Family 10h processor

---

### Post by matt_symes on 2012-05-20
Hi

Open a terminal and type

```
cat /proc/cpuinfo
```

Post the results back here.

Kind regards

---

### Post by Jerry421 on 2012-05-24
jerry@jerry-HP-Pavilion-dv6-Notebook-PC:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 18
model           : 1
model name      : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping        : 0
microcode       : 0x300000f
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips        : 2994.49
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 18
model           : 1
model name      : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping        : 0
microcode       : 0x300000f
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips        : 2994.54
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor       : 2
vendor_id       : AuthenticAMD
cpu family      : 18
model           : 1
model name      : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping        : 0
microcode       : 0x300000f
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips        : 2994.58
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor       : 3
vendor_id       : AuthenticAMD
cpu family      : 18
model           : 1
model name      : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping        : 0
microcode       : 0x300000f
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
apicid          : 3
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
bogomips        : 2994.56
TLB size        : 1536 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

---

### Post by matt_symes on 2012-05-25
Hi

> Warning: No AMD Family 10h processor

=> 16 decimal

> cpu family : 18

I'm pretty sure that's the problem.

Kind regards

---

### Post by Jerry421 on 2012-05-25
Thanks Matt so what command would i need to run to get this to work on my cpu or are you saying its not supported?

---

### Post by mörgæs on 2012-05-25
Moved to Hardware and Laptops.

---

### Post by matt_symes on 2012-05-25
Hi

> **Jerry421 said:**
> Thanks Matt so what command would i need to run to get this to work on my cpu or are you saying its not supported?

I assume it's not supported although i would have to research it to make sure (as that is an assumption).

From the website you referenced i the first post.

> It is intended for AMD Family 10h (aka K10) CPU's (e.g. Phenom, Phenom II)

I think your processor family may be unsupported :(. You need to double check though.

Also, i did assume that 10h => 16 ({hex to decimal} <= was my main assumption as 10h might be the name of the chip) and your family processor 18 were not compatible. 

Did that last statement make any sense ????? :)

Kind regards

---

### Post by Jerry421 on 2012-05-25
yes thank you

---

### Post by Rebelli0us on 2012-06-14
Thanks Matt. I'm very handy with k10stat but k10ctl has no GUI and it looks dangerous to just experiment.


```
**ls -l /dev/cpu/*/msr**
crw------- 1 root root 202, 0 2012-06-14 11:09 /dev/cpu/0/msr
crw------- 1 root root 202, 1 2012-06-14 11:09 /dev/cpu/1/msr
crw------- 1 root root 202, 2 2012-06-14 11:09 /dev/cpu/2/msr
crw------- 1 root root 202, 3 2012-06-14 11:09 /dev/cpu/3/msr
**ls -l /proc/bus/pci/00/18.3**
-rw-r--r-- 1 root root 4096 2012-06-14 11:10 /proc/bus/pci/00/18.3
```

For my 965BE

```
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3
VID interface mode: serial

CPU0
Current P-State: 3      Fastest P-State: 0
               NbVid   NbDid  CpuVid  CpuDid  CpuFid           UNb   CpuMult      UCpu     PCore
P-State 0:        36       0       8       0      18      1100.0mV  17.00000  1450.0mV   30450mW
P-State 1:        36       0      16       0      11      1100.0mV  13.50000  1350.0mV   20385mW
P-State 2:        36       0      24       0       6      1100.0mV  11.00000  1250.0mV   13625mW
P-State 3:        36       0      38       1       0      1100.0mV   4.00000  1075.0mV    4730mW
Low Limit:       124       1     124                         0.0mV   0.50000     0.0mV
High Limit:        0       1       0                      1550.0mV   0.00000  1550.0mV
Target:           36       0      38       1       0      1100.0mV   4.00000  1075.0mV
Current:          36       0      38       1       0      1100.0mV   4.00000  1075.0mV

.....

```

This particular cpu has a high default voltage 1.45 (low leakage?) but runs very stable at 1.3v. So here are the 4 p-states I want to set, got these from cpu-z log:

```
     P-State	FID 0x12 - VID 0x14 - IDD 21 (17.00x - 1.300 V)
     P-State	FID 0xB - VID 0x1C - IDD 15 (13.50x - 1.200 V)
     P-State	FID 0x6 - VID 0x24 - IDD 11 (11.00x - 1.100 V)
     P-State	FID 0x100 - VID 0x34 - IDD 4 (4.00x - 0.900 V)
 
```

It seems that k10ctl command line expects decimal? Looks like 4 commands are needed, one for each p-state:

k10ctl 0-3 **0** -cf XX -cv YY -cd ZZ
k10ctl 0-3 **1** -cf XX -cv YY -cd ZZ
k10ctl 0-3 **2** -cf XX -cv YY -cd ZZ
k10ctl 0-3 **3** -cf XX -cv YY -cd ZZ

where xx, yy, zz are decimal values form my table above?

---

### Post by matt_symes on 2012-06-14
Hi Rebellous.

> I'm very handy with k10stat but k10ctl has no GUI and it looks dangerous to just experiment.

Agreed.

> It seems that k10ctl command line expects decimal?

Yes. There are no hex values in the examples on the web page and for the commands you ran.

Is there any readme with it with more info ?

> Looks like 4 commands are needed, one for each p-state:

Yes. That's also what i think.

> where xx, yy, zz are decimal values form my table above?

To be honest, i would have to do some reading up on this to be 100% sure. I will try tonight.

Kind regards

---

### Post by Rebelli0us on 2012-06-14
ok success, thanks Matt for the inspiration.

I had to boot Windows to see how k10stat is working. Since I'm undervolting, I only need to change CpuVid, so 4 commands:

```
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 0 -cv 20
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 1 -cv 28
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 2 -cv 36
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 3 -cv 52
```

and the end result, we go form the default voltage to undervolted, same performance much less wattage:

```
**Default**

		NbVid   NbDid  CpuVid  CpuDid  CpuFid           UNb   CpuMult      UCpu     PCore
P-State 0:        36       0       8       0      18      1100.0mV  17.00000  1450.0mV   30450mW
P-State 1:        36       0      16       0      11      1100.0mV  13.50000  1350.0mV   20385mW
P-State 2:        36       0      24       0       6      1100.0mV  11.00000  1250.0mV   13625mW
P-State 3:        36       0      38       1       0      1100.0mV   4.00000  1075.0mV    4730mW

**Undervolted**

               NbVid   NbDid  CpuVid  CpuDid  CpuFid           UNb   CpuMult      UCpu     PCore
P-State 0:        36       0      20       0      18      1100.0mV  17.00000  1300.0mV   27300mW
P-State 1:        36       0      28       0      11      1100.0mV  13.50000  1200.0mV   18120mW
P-State 2:        36       0      36       0       6      1100.0mV  11.00000  1100.0mV   11990mW
P-State 3:        36       0      52       1       0      1100.0mV   4.00000   900.0mV    3960mW
```


How do I run these commands every time Ubuntu boots up? :popcorn:

---

### Post by matt_symes on 2012-06-14
Hi

> How do I run these commands every time Ubuntu boots up

One way is to add them to

```
/etc/rc.local
```

before the *exit 0;* command.

EDIT: @Rebelli0us. Keep us informed on how it works please :D

Kind regards

---

### Post by Rebelli0us on 2012-06-14
Matt, CPU registers clear when you suspend/resume S3, so how about I put the 4 commands in **/etc/rc.local** , that should refresh on resume?

```
gksudo gedit /etc/rc.local
```

and add at the end:

```
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 0 -cv 20
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 1 -cv 28
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 2 -cv 36
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 3 -cv 52
```

then

```
sudo modprobe msr
```

should probably go in **/etc/modules** because it only needs to load once per session, just like my Wii remote. Correct?

---

### Post by matt_symes on 2012-06-14
Hi

> **Rebelli0us said:**
> Matt, CPU registers clear when you suspend/resume S3, so how about I put the 4 commands in **/etc/rc.local** , that should refresh on resume?

```
gksudo gedit /etc/rc.local
```

and add at the end:

```
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 0 -cv 20
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 1 -cv 28
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 2 -cv 36
sudo /home/bonky/Downloads/k10ctl/k10ctl 0-3 3 -cv 52
```


For suspend and hibernate, create a file in /etc/pm/sleep.d and hook into resume|thaw.

Something along the lines of....

```
#!/bin/sh

case "$1" in
        thaw|resume)
                /home/bonky/Downloads/k10ctl/k10ctl 0-3 0 -cv 20;
                /home/bonky/Downloads/k10ctl/k10ctl 0-3 1 -cv 28;
                /home/bonky/Downloads/k10ctl/k10ctl 0-3 2 -cv 36;
                /home/bonky/Downloads/k10ctl/k10ctl 0-3 3 -cv 52;
                ;;
esac
```

Remember to prepend the filename with a number for priority in the script sequence.

Make sure the script is executable.

```
chmod 755 /etc/pm/<filename>.sh
```

> 
then

```
sudo modprobe msr
```

should probably go in **/etc/modules** because it only needs to load once per session, just like my Wii remote. Correct?

Yep. Add it to /etc/modules.

Post back on any errors and efficacy.

Kind regards

---

### Post by Rebelli0us on 2012-06-15
Thanks Matt

With the 4 commands in **/etc/rc.local** it worked OK on bootup but stopped working after resume from S3.

So I created **/etc/pm/sleep.d/10_k10ctl.sh** exactly as you posted above. Now it works always -- success!

So the identical commands are needed in BOTH **/etc/rc.local** and **/etc/pm/sleep.d/10_k10ctl.sh** for this to work. Correct?

A GUI would be nice for k10ctl, at least an easy way to know CpuVid,  &#8236;CpuDid and &#8236;CpuFid for each p-state. I used cpu-z in windows and checked the log. In my case I went from this

```
     P-State	FID 0x12 - VID 0x08 - IDD 21 (17.00x - 1.450 V)
     P-State	FID 0xB - VID 0x10 - IDD 15 (13.50x - 1.350 V)
     P-State	FID 0x6 - VID 0x18 - IDD 11 (11.00x - 1.250 V)
     P-State	FID 0x100 - VID 0x26 - IDD 4 (4.00x - 1.075 V)
```

to this

```
     P-State	FID 0x12 - VID 0x14 - IDD 21 (17.00x - 1.300 V)
     P-State	FID 0xB - VID 0x1C - IDD 15 (13.50x - 1.200 V)
     P-State	FID 0x6 - VID 0x24 - IDD 11 (11.00x - 1.100 V)
     P-State	FID 0x100 - VID 0x34 - IDD 4 (4.00x - 0.900 V)
```

To obtain the CpuVid for the command lines I converted the VID column from the 2nd table (above) to decimal (**20 28 36 52**). CPU wattage and temperature dropped in all p-sates.

Then there is the question of serial vs. parallel VID interface mode. Mine is serial though I've no idea what it means. Should I? :lolflag:

---

### Post by matt_symes on 2012-06-16
Hi Rebellious.

I'm glad it's working. Nice job ! :popcorn:

> So the identical commands are needed in BOTH /etc/rc.local and /etc/pm/sleep.d/10_k10ctl.sh for this to work. Correct?

Yes. It's required in both.

> Mine is serial though I've no idea what it means. Should I? 

No you don't need to know what it is, just what you have.

Kind regards

---

### Post by Rebelli0us on 2012-06-19
Thanks Matt, I couldn't have done it without you. Do you know how to do this for Intel CPUs?

---

### Post by matt_symes on 2012-06-19
Hi

> **Rebelli0us said:**
> Thanks Matt, I couldn't have done it without you.

No problem. I think you had a pretty good idea of what are were doing though.

> Do you know how to do this for Intel CPUs?

To be honest, i have never researched this as i have used AMD for years and years (all the way back to the K6).

I kind of like gunning for the underdog :)

If you want to do this for Intel, the first thing would be to see if there was a kernel module available to actually do it.

I tend to just research the tech i have and the tech i consider buying due to limited time etc.

If you can find one then i will gladly help out :) 

Kind regards

---

### Post by Rebelli0us on 2012-12-14
Matt, I'm on a different machine but overclock is not working. It's a Phenom II X2 550 Processor and it will not go above stock frequency!

The following commands work properly

```
/usr/local/bin/k10ctl 0-1 0 -cv 12 -cf 20
/usr/local/bin/k10ctl 0-1 1 -cv 28 
/usr/local/bin/k10ctl 0-1 2 -cv 36
/usr/local/bin/k10ctl 0-1 3 -cv 52

```

And k10ctl reports an overclock in P-State 0 from 3.1 stock to 3.6 GHz while under-volting P-States 1-3


```
Current P-State: 3      Fastest P-State: 0
               NbVid   NbDid  CpuVid  CpuDid  CpuFid           UNb   CpuMult      UCpu     PCore
P-State 0:        36       0      12       0      20      1100.0mV  18.00000  1400.0mV   44800mW
P-State 1:        36       0      28       0       8      1100.0mV  12.00000  1200.0mV   28080mW
P-State 2:        36       0      36       0       3      1100.0mV   9.50000  1100.0mV   20790mW
P-State 3:        36       0      52       1       0      1100.0mV   4.00000   900.0mV   11070mW
Low Limit:       124       1     124                         0.0mV   0.50000     0.0mV
High Limit:        0       1       0                      1550.0mV   0.00000  1550.0mV
Target:           36       0      52       1       0      1100.0mV   4.00000   900.0mV
Current:          36       0      12       1       0      1100.0mV   4.00000  1400.0mV
```


But the CPU frequency scaling monitor, lscpu and cpuinfo all show that frequency stays at stock 3.1 GHz.  Any ideas?

---

