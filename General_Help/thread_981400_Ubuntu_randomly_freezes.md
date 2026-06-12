---
title: "Ubuntu randomly freezes"
date: 2008-11-13
forum: General Help
---

### Post by ryclegman on 2008-11-13
Hello,

I have been having major trouble with my ubuntu 64bit. Randomly My computer will just freeze, and the lights on my keyboard just start flashing. The mouse doesn't move and you are forced to reboot. I had a 32 bit installation before this and it did the same there. Im not sure why or how it happens, but it will usually when Im doing something like watching you tube videos, or surfing the web.Im not sure why this happens, but its starting to get annoying. It can happen 3 times in a half an hour! Im not sure if its a bug or what, but if theres a solution i wound be very happy to fix this.

Hardware:
500gig sata
MSI mother board
4gigs ddr2 memory
Nvidia Gforce 9600 gt
Intel quad core 64 bit

---

### Post by CLomax on 2008-11-13
I can only think of two things:

1. Your PC is an unsupported Dell, like an old model, they exhibit similar problems.

2. Your 9600GT. Apparently they're faulty. I had one which caused me the same problems until it finally caved in.

Just my two pence.

---

### Post by ryclegman on 2008-11-13
ok.... Its not a dell, I built it myself. Also its weird because my hardware isnt even a year old yet..

---

### Post by ryclegman on 2008-11-13
Are there any other suggestions? This doesn't happen in my windows partion either...

---

### Post by CLomax on 2008-11-14
> **ryclegman said:**
> Are there any other suggestions? This doesn't happen in my windows partion either...

My 9600GT was around 2 months old.

Modern technology for you :rolleyes:

I'm afraid I'm unable to help right now, hopefully someone with more knowledge can and will find this thread.

Good luck with your problem ;).

---

### Post by volaer on 2008-11-14
I almost have the same problem as you are having. My UBUNTU freezes on my laptop but only when i play any kind of movie file including visualization. Though i don't have any problem of watching movie throught the internet. This just happens everytime I use TOTEM or any other video players.

---

### Post by Peter09 on 2008-11-14
This could well be your video drivers.

If you are running Intrepid

1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select 'xfix' from the menu, this may resolve it. (Check 1. after doing this as well)

Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

---

### Post by ryclegman on 2008-11-14
This is what i get from terminal :  

> *-display               
       description: VGA compatible controller
       product: Geforce 9600 GT 512mb
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

And theres nothing in my hardware drivers at all,...

---

### Post by ryclegman on 2008-11-18
This is what i get from terminal :

> 
*-display
description: VGA compatible controller
product: Geforce 9600 GT 512mb
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia
And theres nothing in my hardware drivers at all,...

---

