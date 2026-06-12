---
title: "cpu frequency reported"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by enman on 2005-06-02
I run hoary on a compaq evo n610 with a 1.8 ghz pentium 4m processor.  When I cat /proc/cpuinfo, it reports the processor to be Mobile Intel (R) Pentium (R) 4 - M CPU 1.80 GHz, but the cpu MHz row reports 1196.124. My bios has speedstep disabled.

I don't know if the speed is being reported wrong, or the machine is running at a slower speed. I need help figuring this out.

Thanks.

---

### Post by dave9191 on 2005-06-02
Ubuntu is running a speedstepping program by default. its called powernowd. If you do some processor intensive stuff and check again it should report the speed higher.  

Dave

---

### Post by enman on 2005-06-29
I do not have powernows installed and I have disabled cpu freqency stepping in my bios, but the cpu frequency is still reported 1196 MHz.

---

### Post by Zingam on 2005-06-29
I have mobile pentium 4 and speed stepping does not work by default with Ubuntu for me an I had to install and enabe a special module. I don't think that powernowd supports Pentium 4 by default at all.

So what is reported might not be true. Listen to your fan if it is spinning fast then probably the CPU works at full speed.

---

### Post by dave9191 on 2005-06-30
[QUOTE=Zingam]I have mobile pentium 4 and speed stepping does not work by default with Ubuntu for me an I had to install and enabe a special module. I don't think that powernowd supports Pentium 4 by default at all.

So what is reported might not be true. Listen to your fan if it is spinning fast then probably the CPU works at full speed.[/QUOTE]

I have a centrino laptop, pentium 4 M. speed steeping works perfectly. 

And enman, if you did a fefault ubunut install you will have powernowd installed. Make sure that its not running. And that there are no other programs that might be controlling the cpu speed.

---

### Post by Zingam on 2005-06-30
[QUOTE=dave9191]I have a centrino laptop, pentium 4 M. speed steeping works perfectly. 

And enman, if you did a fefault ubunut install you will have powernowd installed. Make sure that its not running. And that there are no other programs that might be controlling the cpu speed.[/QUOTE]
 Centrino means Pentium M, which is something completely different from a Mobile Pentium 4.

Mobile Pentium 4 is a mobile version of the Pentium 4 processor, which is based on a newer architecture called NetBurst, if I'm not mistaken.
Pentium M is completely different from Pentium 4 and is based on Pentium III.

Do not mix up both processors!

Powernowd supports AMD and Pentium M but not Pentium 4. You need to install a module for it to work \I don't remember which one. I need to look up\.

---

### Post by dave9191 on 2005-07-01
Hmm, you learn something new everyday huh :)

---

### Post by enman on 2005-07-01
Thanks zingam. My fan seems to be running at full speed. I do not want my cpu to be stepped so I will not install the extra module. But it would still be nice if ubuntu reported the correct speed of the cpu.

---

### Post by dave9191 on 2005-07-02
[QUOTE=enman]Thanks zingam. My fan seems to be running at full speed. I do not want my cpu to be stepped so I will not install the extra module. But it would still be nice if ubuntu reported the correct speed of the cpu.[/QUOTE]

Hey, can I ask you why you dont want you cpu speed stepped ? Since you have a P4 m, Im guessing its a laptop, having you cpu running at full speed uses up more battery and it gets hotter quicker, and in some cases close to dangerous temps.

---

### Post by taldones on 2005-07-22
If you have speed-stepping disabled in your bios, your processor is probably running at its lowest possible frequency state. I'm running a mobile pentium 4 at 3.06 GHz on an Inspiron 5150 and if I disable speed-stepping in the bios, the processor drops down to 1.56 gHz.

I wouldn't recommend running it at full speed all the time though... your laptop may not even be designed to dump the amount of heat that your processor would put out, and besides, it's just a waste of battery power.

--taldones

---

### Post by luca_linux on 2005-07-22
The module's name is something like p4_clock...

---

