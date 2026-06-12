---
title: "ran various nosplash and found stopping point"
date: 2008-10-17
forum: Hardware
---

### Post by wcwashington on 2008-10-17
it seems everything loads after i ran a nosplash in verbose mode and i found that (btw i used wubu to install)

[159.619612] input: pcspeaker as /devices/platform/pcspkr/input/input 8

^^^^ this is the stopping point where it wont go anywhere...its a sound card problem is there anyway around this???? 

i have tried the other options under the grub4dos like the acpi workaround and live cd , visual problems....  


i think under the acpi workaround 

it gave a 

sdhci: slot0: unknown controller version (16) you may experience problems
mmc0: sdaci at 0xffbfe800 irq 5 pio

i am running an everex step note sa2053t and have tried the everex forums there but they suck... im gonna try to google this problem out stopping here see if you guys had any suggestions

---

### Post by wcwashington on 2008-10-17
found this 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187671](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187671)

im wondering if i have to run an older version i really havent read this through just skimmed ..... gotta catch some z's this caffiene isnt doing its job :P

---

### Post by eldragon on 2008-10-19
hmm, in order to be able to run linux through a livecd, you will have to build your own live cd, with its custom kernel with the patch uploaded here: [http://bugzilla.kernel.org/show_bug.cgi?id=10231](http://bugzilla.kernel.org/show_bug.cgi?id=10231) ...way beyond a begginer's skills. and it will probably require a running linux install in order to achieve it.

so, you have two options. try and install it the hard way and hope you dont break vista....(which will probably wont happen if you are careful enough) or just wait and hope the patch gets included in the intrepid ibex release.

considering the specs of the notebook, keeping vista inside seems like a waste of resources, but thats me :D

---

