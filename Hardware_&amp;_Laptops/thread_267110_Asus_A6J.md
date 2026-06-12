---
title: "Asus A6J"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by Reshin on 2006-09-28
Okay, lessee...

- Either cpu or GPU fan is going full speed all the time. Why? :-? 
- Display blackouts at times and sometimes screensaver turns on too soon. Similar effect on kde is that it black outs and message says Display: LCD on. Annoing ](*,)

---

### Post by Reshin on 2006-09-29
Anyone? :(

---

### Post by dwight on 2006-09-29
I have an Asus A6Jc. Should be very similar to what you have. Haven't had any problems with my fans, so can't comment on that. But I did have issues with this "LCD on" message popping up from time to time. Especially in Kubuntu 6.06. Now I'm using Eft and haven't experienced that problem anymore.

---

### Post by arkangel on 2006-09-29
is your processor duo  or solo ,  which kernel and which version are you using (386 or 686 --uname -r in a console -- )  which video card do you have and the drivers are properly working 

the last post on[ this page]("http://ubuntuforums.org/showthread.php?t=210173&page=4") can help you


My centrino was also friying until i switched to kernel 386

---

### Post by Reshin on 2006-09-29
> **arkangel said:**
> is your processor duo  or solo ,  which kernel and which version are you using (386 or 686 --uname -r in a console -- )  which video card do you have and the drivers are properly working 

the last post on[ this page]("http://ubuntuforums.org/showthread.php?t=210173&page=4") can help you


My centrino was also friying until i switched to kernel 386

Centrino duo. I was using 686-smp. Not sure if it did that with 386 :-k Have to try again

---

### Post by Reshin on 2006-09-29
did cat /proc/cpuinfo and this is what i got > ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1829.253
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 3663.60


When I did that on Knoppix, it gave me that two times meaning it found the dual cores. On ubuntu, it showed that only once which means it found only the first core. Any way to make it recognice it as dual core?

---

### Post by arkangel on 2006-09-29
weird  , in my case I  only have  one core so 386 works for me ok,  but  for double core support you need the 686 smp  so try to reinstall it 
sudo aptitude  reinstall linux-686-smp
maybe you have luck  this time 
[here]("http://packages.ubuntu.com/dapper/base/linux-686-smp") the dependncies 

also  try to use the latest  [ati  driver]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27") ,(you have an ati x1600 ,dont you? ) i think the support for  that card was from  8.26 or 8.27 and onwards

as you said  cat /proc/cpuinfo should list  twice for proc 0 and proc 1

---

### Post by Reshin on 2006-09-30
Yeah, it showed both when I installed regular 686. Mayby I missed something but -smp seemed to be a meta-package for same files as regular 686 :-k Didn't do anything special when I installed it.

And my laptop kept heating no matter what kernel I was using.

---

### Post by Reshin on 2006-10-09
Go figure. Hard drive was busted. Have to send it for repaires

---

