---
title: "Best hardware configuration for running a VM server"
date: 2012-04-08
forum: Hardware
---

### Post by KyleThe49er on 2012-04-08
I'm drafting a hardware configuration to create a virtual machine server. The server will be Ubuntu server based (with virtualbox) and will host 3 - 4 Windows guests (XP). The goal is for the server to be 'headless'. I'm familiar with the hardware, however I do not know what is/isn't necessary for multiple virtual machines to run effeciently simutaneously. So far I have chosen an AMD FX-8120 CPU (8-cores), MSI 970A-G46 motherboard, MSI GTX 460 graphics card, a SATA III Crucial SSD, 12GB DDR3-1600 memory. I've also got additional hard disks for backup purposes, and a SeaSonic power supply. 

Questions:
1. Is more CPU cores or a higher clock speed better?
2. Will a better/faster GPU help the performace of the VM's?

Thanks for any thoughts.

---

### Post by rjparker1 on 2012-04-08
There is no "best" configuration for hardware, only that it SUPPORTS virtualization.

The ONLY feature you need is the ability to run x64 VM, and that will enable when you go into the BIOS and change virtualization to on.  ANY platform (even without this feature) can virtualize any 32-bit VM.

GPU will have ZERO impact on VM performance, if you want to run games, you don't do it in a VM, dual boot.  if you MUST run games in a VM, the GPU will be hampered by the fact that VM's do not have direct hardware access, so the memory and CPU are running through a hyper-visor (which is a software layer) and the game will not perform as well (average VM over head is around 15 to 20%).  Overhead is the amount of system resource that you will lose when running VM's, so if you run a process on a native hardware that is 3Ghz expect to get 15% less performance (maybe even less) simply by putting that same application in a VM.

For CPU MORE core is better than faster core, because at any time ANY one of your CPU can be maxed, don't care how fast they are, if they are pegged, they will not be able to provide more cycle for additional processes, so get 6 core (per socket) if possible, QUAD at the very least.

Even a measley 1.6ghz quad will run circles around a dual 3Ghz any day (depending on load).  Bottom line is more cores is better than faster (est).

The software doesn't matter.  I will repeat that the virtualization host software does NOT matter.  The virtualization and processing power takes place AT the hardware layer.

So use ANY host software you want, they will ALL perform the same.  The only difference is features and extras (like snapshot, or recording VM session, etc..).

Virtual box is good, however, be advised that *.vdi format that Virtual box creates by defaul is NOT compatible with other products, therefore I suggest you use a VM Ware product *OR* create the VM using the *.vmdk format.

Later if you want to make it portable, you can do it easily

---

