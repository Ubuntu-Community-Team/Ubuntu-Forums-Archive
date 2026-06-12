---
title: "PS/2 mouse not recognized by xubuntu!"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by asbesto on 2006-09-26
Hi everyone,

i have this weird problem and i don't know how to solve it. 

My system is an ASUS K8N4-E mainboard and I simply connected a ps/2 mouse as i have done for years on my linux boxes

then this happens:

[INDENT]root@giove:~# uname -a
Linux giove 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
root@giove:~# cat /proc/bus/input/devices 
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 evbug 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 evbug 
B: EV=40001
B: SND=6
[/INDENT]

So, there's no way to use my PS/2 mouse here, and i really don't know how to solve this. 

The system is a fresh installed xubuntu with an ATI RADEON card using proprietary drivers; also, Xorg will start but mouse is obviously not working.

Any hint ? :-?

---

### Post by asbesto on 2006-09-27
no answer at all... hmmm, this forum's pretty useless :confused: 

anyway:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34651]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34651")

is definitively a kernel BUG in the xubuntu distro, affecting ASUS motherboards with nVIDIA chipset. 

](*,)

---

