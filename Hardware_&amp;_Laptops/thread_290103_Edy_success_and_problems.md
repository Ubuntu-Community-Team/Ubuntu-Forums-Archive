---
title: "Edy success and problems"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by thila on 2006-10-31
Got my brand new dell 6400 this morning, decided to install edge after seeing the bloatware on the new machine!! Here is the status - Any suggestions for issue 1 and 4 are welcome and greatly appreciated:

Installation went well except for the following:

1) Even though I get awsome resolution, I need a way to reduce the brightness - The function keys to reduce the brightness dont work. Any suggestions?? I had tto install the 915resolution.

2) WIFI is the major problem, but for now the Wired connection works  - so not a biggie, I can wait for the fix. The gnome network manger does not even recgonize my wireless.

3) The temp is not bad, same as my prev vaio laptop.

4) I am not sure if my DUAL core is recognized or not. In /proc/cpuinfo I see  two sets of entires (processor = 0 and 1) with both having 1 sibling, which I think is dual core - is there anyother way to check if my dual core is seleccted? Following is my cpuinfo output. Any suggestions??

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3328.73

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no

---

### Post by tribaal on 2006-10-31
A few pointers, and a suggestion:

Suggestion: You should try to post only one question per post, as it will greatly improve response time, and you'll be able to ask the specific question in the subforum it's supposed to go in exactly. Also, people having the same problem will find the answer more easily. Not a big deal, but it's generally considered a better way to post.

Enough now, let's go with the pointers :)

For 2): Make sure your WiFi card is reported as "activated" under System > Administration > Network before you install NetworkManager. I cannot explain *why*, but this is how I got my wireless card to work on my rig... Maybe someone else can explain better (hopefully). 
Also, make sure your hardware WiFi powerswitch is turned on ;) I spent hours cursing before realizing it was off, once :)

For 3) just a tip, but I personally love this little applet: "emifreq-applet". It helps monitor your CPU scaling and temperature... I just love it. Not sure how it works on multicores, though, but it's definately worth giving a try.

For 4), the default kernel image in Edgy is multicore-aware, so you're all good :) It used to be a feature that required a kernel download (nothing scary, but had to be done manually), but now it's included by default.

Hope this helps at all... 

Welcome aboard :)

- trib'

---

