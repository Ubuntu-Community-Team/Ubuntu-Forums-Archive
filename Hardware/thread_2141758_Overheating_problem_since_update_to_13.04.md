---
title: "Overheating problem since update to 13.04"
date: 2013-05-03
forum: Hardware
---

### Post by Tews33 on 2013-05-03
Hi,

I've recently updated my ubuntu from 12.10 to 13.04 and since then the fan seems to have been stuck to 100%. It's unbearably noisy.
I've browsed through quite a lot of discussion whitout success.

I've installed tlp and it seems that my CPU is about 37°C, so I'm not sure if the problem come from an overheat or from a "fan management speed".
I've tried to get a newer version of the kernel (3.9), no change.
I've tried to use the kernel version I had with ubuntu 12.10 (3.5), no change neither

When I tried to boot on windows 7, same problem.
Actually, even if I stay on the grub menu for a few seconds, my fan goes from what used to be normal to full speed.
So maybe the problem comes from more basic stuff.

My configuration :
System         = Medion   E6217 (a laptop)BIOS           = 202
Release        = Ubuntu 13.04
Kernel         = 3.9.0-030900-generic i686
Graphics     = intel i915 (integrated)


I can provide other informations if you need.

Thanks for your help =/

Edit : I don't believe the problem could be from there, but here is some boot-info : [http://paste.ubuntu.com/5629995/](http://paste.ubuntu.com/5629995/)

---

### Post by Tews33 on 2013-05-04
Alright, maybe this problem seems to be a little too common for you guys to answer =/

I'll try to highlight the differences from every thread I've checked so far :
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]No matter what OS I boot on, or even I I stay on the GRUB, the fan goes full speed.[/SIZE]
[LIST]
[*][SIZE=2]maybe something to do with the bios then ?[/SIZE]
[/LIST]

[*][SIZE=2]the fan is on regular speed during the first 20 sec and then goes full speed and stay consistent after that.[/SIZE]
[*][SIZE=2]this happened just after I updated from ubuntu 12.10 to 13.04, so I doubt it is a "regular maintenance problem" like dust accumulation, although it's still possible.[/SIZE]
[/LIST]

I'm not even sure anymore if the problem is overheating which cause the fan to go full speed or if something has been messed up in the fan speed control.
I don't know either if the designated fan is the one on the CPU or the GPU.


Any slight bit of hope would be greatly appreciated, or any useful link, or something I could look into, or well, anything :(

---

### Post by Yellow Pasque on 2013-05-04
37C is not overheating, so fan control is messed up if the fan is running full speed at that temp.

> I don't know either if the designated fan is the one on the CPU or the GPU.
What is your GPU and what driver are you using?

---

### Post by SuperFreak on 2013-05-04
Check fan settings in BIOS or UEFI if you use that.

---

### Post by Tews33 on 2013-05-06
Thanks for your answers !

Here is the output of the ```
tlp-stat
``` command, in case it may be an obvious missconfiguration : [http://paste.ubuntu.com/5637492/](http://paste.ubuntu.com/5637492/)

@SuperFreak
I've spent quite a while in my BIOS since that happened, no such control option, or any mention of fan in there. Merely a few information about my processor clock speed.

@Temüjin
After a few checks, it's something called "Intel® HD Graphics" I think it's probably something integrated on the motherboard. So it's not impossible that I actually have a single fan.
After your answer, I went on the intel website to find the driver they provide, but the newest was intended for ubuntu 12.10 (wich didn't work, I tried anyway).
Maybe I should try to compile it on my own but I have little idea on how to do that so it would probably takes me a couple hours more.

If I can't find any solution, I'll try to install the 12.04 or a more "stable" distrib, but I'm not even sure that would fix the problem.


Update : I formatted what I thought was the guilty partition, but no change. I ran dry of any possible solution right now ...
Somebody please help me =/

---

### Post by Tews33 on 2013-05-14
Hey !

So my problem is still there, and still quite anoying.

I found this [http://support.apple.com/kb/HT3964](http://support.apple.com/kb/HT3964) and almost every symptom is there !

PROBLEM : I don't have a mac ... but still a intel CPU though

Anyone ? Do you know something equivalent for my medion e6217 ?

---

### Post by Tews33 on 2013-05-15
up

---

### Post by Obi123 on 2013-05-15
I have the same problem since today. Left he PC on lock and when I came back the fan was at full speed. But I don't have an Intel, but instead an AMD Athlon II X2 215. It started making the noise today and I have no idea what to do.

---

### Post by Tews33 on 2013-05-16
Is the PC equivalent for the mac SMC (system management controller) is the BIOS? Should I try to reset it ? what are the risques ?

---

