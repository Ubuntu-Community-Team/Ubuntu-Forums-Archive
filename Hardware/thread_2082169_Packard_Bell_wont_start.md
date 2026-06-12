---
title: "Packard Bell wont start"
date: 2012-11-08
forum: Hardware
---

### Post by pjy on 2012-11-08
Hi,

I installed ubuntu server to my Packard bell imedia S (desktop pc) ubuntu. Everything went well untill I need to restart pc after installation. It frozen so I needed do cold boot manually(press few seconds several time). Now It wont start. I tried install again but same dejavu.
In safemode I can see follow messages and after nothing other doesn't help than cold boot:
[IMG]http://dl.dropbox.com/u/338905/ubuntu.jpg[/IMG]

My pc specs are:
Packard bell iMedia S2100
Windows 7 Home Premium 64-bit
AMD e1-1200 processor
AMD Radeon HD 7310 graphics
500GB Hard Drive
4GB DDR3 memory
DVD-super Multi drive
Integrated Lan 10/100/1000
Output: HDMI/VGA

This is planned for server use so I don't need any X.

---

### Post by pjy on 2012-11-16
Hi,

I resolved the problem.  I edited grub config 
quiet splash acpi=enable pci=noacpi pci=assign-busse acpi=ht

Thanks for active ubuntu community :guitar:

---

