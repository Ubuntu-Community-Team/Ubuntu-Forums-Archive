---
title: "Compiz broke my install"
date: 2008-10-09
forum: General Help
---

### Post by ryry46d9 on 2008-10-09
I was reading /play some people wanted output of Compiz ... so I thought I would try it to see what I showed well after one hour Compiz locked up on me  I had no out put from the consel so like a dummy I closed the window instead ctrl-c then ctrl-d ...well the hole computer became non-responsive so I ctrl-alt-backspace and came back too see picture:[IMG]http://i280.photobucket.com/albums/kk185/docryry/Compiz.png 

I reinstalled AMSN but its still a no go 

any ideas on the gome error?

---

### Post by ryry46d9 on 2008-10-09
some info that I forgot but the picture should enplane it 

ubuntu 8.04.1 32bit had to many problems with 64bit and flash/java

 description: Motherboard
       product: A8V-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890

*-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx  mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc

*-display UNCLAIMED
                description: VGA compatible controller
                product: K8M890 [Chrome9] Integrated Video
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
mxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc

---

### Post by loomsen on 2008-10-09
> ubuntu 8.04.1 32bit had to many problems with 64bit and flash/java

Which most likely caused the freeze. However, why didnt you simply install the 64bit flash plugin?(see attachement)

And for your next freeze, you might want to be prepared and familiar with some SysRq magic :D

Alt + PrintScreen + (K) REISUB

is a smoother way to make sure nothing is left corrupt. At least it didnt disappoint me so far, leaving my fs broken or sth.

(the K added in brackets is optional, however I use it; it is killall processes; google will tell u about the other letters if you're interested in)

---

### Post by ryry46d9 on 2008-10-09
I have 32bit ubuntu right now . I might go back to 64bit if I ever go past 4GB ram

---

### Post by pluckypigeon on 2008-10-18
> **ryry46d9 said:**
> I was reading /play some people wanted output of Compiz ... so I thought I would try it to see what I showed well after one hour Compiz locked up on me  I had no out put from the consel so like a dummy I closed the window instead ctrl-c then ctrl-d ...well the hole computer became non-responsive so I ctrl-alt-backspace and came back too see picture:[IMG]http://i280.photobucket.com/albums/kk185/docryry/Compiz.png 

I reinstalled AMSN but its still a no go 

any ideas on the gome error?

I get this same problem accept I can't ctrl-alt-backspace or anything else. I have to restart it from the restart button.

Compiz completely locks up on me, it never done this under hardy but now I have upgraded it doesn't work anymore.

Here's some info

```


vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)



```

---

### Post by loomsen on 2008-10-18
> **pluckypigeon said:**
>  I have to restart it from the restart button.

it never done this under hardy but now I have upgraded it doesn't work anymore.


1. Read my post above and try it prior to restarting from the restart button

2. Don't upgrade to beta versions. Clean installs will work from alphas usually, I'm using Intrepid since Alpha 3. But upgrading isn't recommended because it most likely leaves broken packages.

---

### Post by pluckypigeon on 2008-10-18
> **loomsen said:**
> 1. Read my post above and try it prior to restarting from the restart button

2. Don't upgrade to beta versions. Clean installs will work from alphas usually, I'm using Intrepid since Alpha 3. But upgrading isn't recommended because it most likely leaves broken packages.

I've tried that ALT+PRINTSCRN+REISUB and it doesn't work.

---

