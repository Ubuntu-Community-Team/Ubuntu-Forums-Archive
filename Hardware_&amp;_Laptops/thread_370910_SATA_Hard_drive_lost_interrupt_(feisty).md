---
title: "SATA Hard drive lost interrupt (feisty)"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by Curtisc on 2007-02-26
I've got Feisty installed on my IDE hard drive, and that's all well and good, but I'd like to use my SATA drive as well.  When I boot, I get this message:
```
[ 29.435837] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 19
[ 55.735467] hdg: lost interrupt
[ 85.664295] hdg: lost interrupt
[ 105.620841] hdg: dma_timer_expiry: dma status == 0x24
[ 115.597122] hdg: DMA interrupt recovery
[ 115.597126] hdg: lost interrupt
[ 135.549676] hdg: dma_timer_expiry: dma status == 0x24
[ 145.525949] hdg: DMA interrupt recovery
[ 145.525953] hdg: lost interrupt
[ 165.478502] hdg: dma_timer_expiry: dma status == 0x24
[ 175.454779] hdg: DMA interrupt recovery
[ 175.454784] hdg: lost interrupt
[ 195.407334] hdg: dma_timer_expiry: dma status == 0x24
[ 205.383613] hdg: DMA interrupt recovery
[ 205.383619] hdg: lost interrupt
```
The boot process takes about 5-10 minutes, and even once it's booted I can't get gparted to recognize the SATA drive (hdg).  So far, I've just been disabling it by adding "hdg=noprobe" to my boot options, but that's not much of a solution.  I briefly tried openSUSE, and that had no problem installing to the SATA drive, so I don't think it's a hardware issue.  Any help would be greatly appreciated, thanks!

---

### Post by Curtisc on 2007-02-26
Shameless bump... any thoughts?

---

### Post by frafu on 2007-03-03
Hello, 

I have a similar problem: 

Edgy Eft is running fine on hda1.

I did a "sudo update-manager -d" to upgrade my second instance of edgy, that is situated on hda2, to feisty and it gives me the same errors as discribed by Curtis. 

My drives: 
hda: ide from Samsung
hdb: ide from Maxtor
hdc: cdrw
hdd: combo
hde: sata from WD
hdf: sata from Samsung

In fact, I get the errors described by Curtis for hde and hdf. 

The motherboard is an ASRock 775i65GV. The connectors for my 6 drives are all provided by the motherboard. 

Francesco

---

### Post by Donald on 2007-03-03
This is due to bug 78288

[https://launchpad.net/ubuntu/+source....20/+bug/78288](https://launchpad.net/ubuntu/+source....20/+bug/78288)

Please add to the bug report the output of

```
lspci -vv
```

and

```
lspci -vvn
```

---

### Post by frafu on 2007-03-03
Hello Donald, 

I have just added the two reports to the corresponding bug in launchpad. 

Your link above does not seem to work; I hope that the following will work: 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78288](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78288)

Finally, the computer in question is again running headless; so I am not able to see the text that appears on the screen when it boots. Could anybody please tell me whether that text gets logged and if so, where I can find it? 


Francesco

---

### Post by Donald on 2007-03-03
Thank you very much, Frafu! Unfortunately this bug does
not get much attention right now, but i hope that will change,
if more people report the problem.
So again, thank you very much. I hope development will
fix this bug soon!

---

### Post by frafu on 2007-03-04
As already said, the computer boots with the irqpoll option; however I wonder whether it is running as it should: 
- there is no trash icon
- the harddisks do not appear on the desktop, nor in the Places menu; however I can browse them by beginning with my home folder in the Places menu. 

The question now is: 
- Is it due to this #78288 bug? 
- Is it because I upgraded a system that was not very clean? 
- Is the missing trash and harddisks icons normal in feisty? (that would be astonishing) 

Finally, the bug thread in launchpad says that there are 3 duplicates. Is there an easy way to find them? 

Francesco

---

### Post by Rog on 2007-03-08
I'm having very similar problems, so far I'm just glad to have found people who share the issue, there's a better chance of fixing it now.

Does everyone experiencing this have their OS installed on an IDE disk, and the problem occurring with a separate SATA disk?  That seems to be a common occurrence.

---

### Post by Reapman on 2007-03-23
Same here, I believe this happened in Edgy with me as well (or something very similar it was awhile ago).  Shame it's not getting much attention.

---

### Post by Rog on 2007-03-23
Fortunately, it has had some attention (from upstream, I believe).  This issue was fixed for me and others in kernel 2.6.20-12.

See [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78288]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78288")

---

