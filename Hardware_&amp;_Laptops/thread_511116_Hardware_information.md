---
title: "Hardware information"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by BDNiner on 2007-07-27
Is there a better program that identifies hardware information in ubuntu? I have a Pentium 4 3.0GHz processor and it is showing in the system monitor that i have two processors. processor 0 and processor 1. I didn't this that intel made a dual core processor for the m478 socket type. I can't seem to find any info about this online. Can someone please advise, tonight i am going to take it out and clean off the paste so that i can see what kind it really is, but i would like to see if i can find out without taking out the processor.

---

### Post by Soybean on 2007-07-27
Anything with hyperthreading also shows up as two processors. It's not actually two cores, it just kind of acts like it in some situations. 

You can type ```
cat /proc/cpuinfo
``` in a terminal to see more information about your processor, but most of it is a little cryptic.

I just compared the output on my desktop (Pentium 4, 3.0Ghz with hyperthreading and only 1 core) with one of our servers (Pentium D, 3.0 Ghz, dual core). While the system with hyperthreading does show two processors ("processor: 0" and "processor: 1"), they both have the same "physical id" of zero. The dual core system's two processors show up with "physical id: 0" and "physical id: 1". 

Also, the "model name" should give some useful info too... I don't think anything with dual cores was ever sold as a "Pentium 4," was it? I thought it was just the Pentium Ds and the Core Duos and so on, but I could be wrong.

---

### Post by BDNiner on 2007-07-27
Thank you, that explanation helped.

---

### Post by squich on 2008-01-17
I need to know my Motherboard type. (full name) Where I can see this?

---

### Post by 00l0 on 2008-06-15
> **squich said:**
> I need to know my Motherboard type. (full name) Where I can see this?

$sudo aptitude install sysinfo

OR
$sudo aptitude install hardinfo

OR
$sudo lshw
(will give you full information of your system, go check the -core:Motherboard section, should be enough, i think) : D

---

