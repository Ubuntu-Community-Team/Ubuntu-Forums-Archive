---
title: "ASUS eee PC 1018p - ACPI Trip Points"
date: 2011-08-10
forum: Hardware
---

### Post by Ocilus on 2011-08-10
I am running Ubuntu 11.04 on a Asus 1018p netbook. I am having trouble getting my CPU fan to spin thus causing my computer to overheat rapidly. I have been doing quite a bit of research online and have tried multiple methods for getting my fans to start working but to no avail. I believe it has to do with my thermal trip zones. Upon typing "acpi -V" into the terminal I get the following

Adapter 0: on-line
Thermal 0: ok, 70.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 98.0 degrees C
Cooling 0: LCD 10 of 10
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

I am not a linux guru so I am not quite sure if this is out of the ordinary but for my trip points to be 98 degrees and 100 degrees seems a bit outrageous. I would like to know a way to modify these trip points or if this is not the problem a little insight into what may be the issue. I appreciate your time.

---

### Post by Ocilus on 2011-08-10
I have attempted changing grub setting in order to trigger fan but this did not yield any results

---

### Post by nanogordo on 2011-12-18
Ocilus, I am having the same issue with my 1018p netbook running Ubuntu 11.04 overheating due to fans not turning on. I've walked through the same steps as you have.

Have you had any success in finding a solution? Does anyone else have any recommendations.

Thanks in advance!

---

### Post by jwalin on 2012-02-17
I want to install Ubuntu on my 1018p this weekend, have these issues been resolved?  I am brand new to all this......I have only installed Ubuntu on my Macbook Pro before, and it worked 90%.

---

