---
title: "hd 3650 agp proprietary driver freezes system"
date: 2011-01-16
forum: Hardware
---

### Post by tekay on 2011-01-16
hello there,

even if I'm running Linux Mint 10 I wanted to post here as well for maybe you have different ideas than the mintforum-guys.

i searched the internet including several forums like ubuntuforum, mintforum, etc. for a solution for about 2 weeks but found absolutely nothing on my particular problem. 
here it is: 

i recently installed mint 10 on my desktop which ran previously with win xp prof. 
installation went without problems until i tried to activate the proprietary driver for my Radeon HD 3650 agp graphics card. 
after reboot everything looked nice, performance was considerably better but not for long. 
the machine just freezes after several minutes after I start firefox for example, sometimes even earlier. I guess it's too resourceful for I don't know...maybe Xorg or grapics card or processor or whatever. After deactivating the proprietary driver and rebooting, everything is fine again with the open-source driver but with far less performance. I cannot activate any visual effects and video playback is rather jerky. 
so...i just don't know what to do...
all the solutions for similar problems weren't working for me, so I'm finally looking for help here.
do you have any ideas? 
btw. I tried to downgrade to mint 9 for maybe it would work there, but had big yet unresolved installation problems with not detecting any package installation files. I dunno maybe the problems are related to each other. 

my specs:
linux mint 10 32bit
athlon XP 3000+ on ASUS A7N8X-E board
550 W power supply
1.5 GB RAM

If you need anything else just let me know. 
First tried Mint 7 on my thinkpad T42 about a year ago. 
that means I'm pretty new to linux but solved any problems until now without further help than the usual forums and bug-posts.

until then
greetings 
TeKay

```
tekay@grummel ~ $ sudo lshw -C display
[sudo] password for tekay: 
  *-display               
       description: VGA compatible controller
       product: RV635 PRO AGP [Radeon HD 3650]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:19 memory:d0000000-dfffffff ioport:c000(size=256) memory:e6000000-e600ffff memory:e5000000-e501ffff

```

---

