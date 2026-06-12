---
title: "unable to install ubuntu"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by sontipheap on 2009-08-06
I can't seem to pass the "apic error; panic timeout " message when trying to install ubuntu 9.04 version onto my desktop.  I have an AMI BIOS and I can't seem to find in the BIOS where to enable or disable the apic option.  Can anyone help me, I have been going crazy for the past few weeks trying to figure out where I went wrong. I know that newer motherboards have moved the timer to a different location thats why the kernel couldn't find it during the installation process.  I have HP Pavilion desktop with AMI BIOS and motherboard( ECS RC410-10-M, HP/COMPAQ name: Asterope-GL8E).

---

### Post by Partyboi2 on 2009-08-06
Hi, try using noapic as a boot option. When you are at the main menu of the Ubuntu cd press "F6" and at the end of the line add ```
noapic
``` then press 'enter' to boot.

---

