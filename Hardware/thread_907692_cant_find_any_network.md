---
title: "cant find any network"
date: 2008-09-01
forum: Hardware
---

### Post by roberth_001 on 2008-09-01
Now, im new to ubuntu, having finally gotten tired of Vista or my current laptop, and being unable to downgrade to XP, of which i was fond. However, despite everything, i am completely unable to connect to my network. I know that my wireless is currently unavailable (i have a packard bell Easynote MX-37) but according to everything i have read, my ethernet should work straight out of the box. I have checked in the hardware information. and my card is shown (SiS 191 Gigabit ethernet adaptor), but its not shown in the network settings, and its thrown me already. I dont consider myself to be particularly stupid, but if this is supposed to be easy linux i think im in over my head...

EDIT: ive just noticed i may have posted this in the wrong setion, so my appologies for screwing up my first post if that is the case)

Another EDIT: Forgot to mention, im using gutsy at the moment, as hardy was having problems with the grpahics, of which i really cant explain off hand. Yes, i have gone horribly worng here already... :)

---

### Post by IntuitiveNipple on 2008-09-01
Can you provide the results of some commands? Start a terminal session via Applications > Accessories > Terminal.

At the prompt issue these commands, then copy (drag-select then Ctrl+Shift+C or Edit > Copy) and paste the commands and their results to a post here:
```

lspci

lsusb 

sudo lshw -C network

ifconfig

iwconfig

```

---

### Post by roberth_001 on 2008-09-01
[quote=terminal]
rob@rob-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)[/quote]
[quote=terminal]rob@rob-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 [/quote] 
[quote=terminal]
rob@rob-laptop:~$ sudo lshw -C network
[sudo] password for rob:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
rob@rob-laptop:~$ [/quote]
[quote=terminal]
rob@rob-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/quote]
[quote=terminal]rob@rob-laptop:~$ iwconfig
lo        no wireless extensions.
[/quote]

And thanks for your help. i feel like such a fool when i move to a new OS...

---

### Post by IntuitiveNipple on 2008-09-01
Hey, don't worry about it. As long as you're willing to learn and explore :)

The reports above, **lshw** especially, show that no driver has claimed (UNCLAIMED) either of the network devices. So it isn't just the AtherosAR5006 WiFi chip-set but also the wired SiS 191 Gigabit Ethernet too.

Lets gather a bit more detailed information about the ID of the devices:
```

lspci -nn

```
That will give us the PCI device IDs, not just the names, which will allow us to find out which driver should be handling them.

Hopefully, with that, [this article will help](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6).

---

### Post by roberth_001 on 2008-09-04
Sorry for late reply, but i have been away for a few days, and only now able to try this. I have followed that guide up until the > make oldconfig, at which point i get the response > make: *** No rule to make target 'oldconfig'. Stop

Any idea where im going wrong ( the kernel is extracted to /me/linux-2.6.22.14 if that matters)

Ignore me, i way forgetting to use cd first...now alls good again

Instead, when i run the command...horrible large log of errors
> rob@rob-laptop:~$ cd /home/rob/linux-2.6.22.14
rob@rob-laptop:~/linux-2.6.22.14$ make oldconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function â&#8364;&#732;usageâ&#8364;&#8482;:
scripts/basic/fixdep.c:131: warning: implicit declaration of function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:131: error: â&#8364;&#732;stderrâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function â&#8364;&#732;exitâ&#8364;&#8482;
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;print_cmdlineâ&#8364;&#8482;:
scripts/basic/fixdep.c:140: warning: implicit declaration of function â&#8364;&#732;printfâ&#8364;&#8482;
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared here (not in a function)
scripts/basic/fixdep.c: In function â&#8364;&#732;grow_configâ&#8364;&#8482;:
scripts/basic/fixdep.c:156: warning: implicit declaration of function â&#8364;&#732;reallocâ&#8364;&#8482;
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function â&#8364;&#732;perrorâ&#8364;&#8482;
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;is_defined_configâ&#8364;&#8482;:
scripts/basic/fixdep.c:174: warning: implicit declaration of function â&#8364;&#732;memcmpâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;define_configâ&#8364;&#8482;:
scripts/basic/fixdep.c:187: warning: implicit declaration of function â&#8364;&#732;memcpyâ&#8364;&#8482;
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memcpyâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;use_configâ&#8364;&#8482;:
scripts/basic/fixdep.c:206: error: â&#8364;&#732;PATH_MAXâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memcpyâ&#8364;&#8482;
scripts/basic/fixdep.c:220: warning: implicit declaration of function â&#8364;&#732;tolowerâ&#8364;&#8482;
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
scripts/basic/fixdep.c:206: warning: unused variable â&#8364;&#732;sâ&#8364;&#8482;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;size_tâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;parse_config_fileâ&#8364;&#8482;:
scripts/basic/fixdep.c:227: error: â&#8364;&#732;lenâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function â&#8364;&#732;ntohlâ&#8364;&#8482;
scripts/basic/fixdep.c:244: warning: implicit declaration of function â&#8364;&#732;isalnumâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;strrcmpâ&#8364;&#8482;:
scripts/basic/fixdep.c:261: warning: implicit declaration of function â&#8364;&#732;strlenâ&#8364;&#8482;
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;do_config_fileâ&#8364;&#8482;:
scripts/basic/fixdep.c:272: error: storage size of â&#8364;&#732;stâ&#8364;&#8482; isnâ&#8364;&#8482;t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function â&#8364;&#732;openâ&#8364;&#8482;
scripts/basic/fixdep.c:276: error: â&#8364;&#732;O_RDONLYâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:278: error: â&#8364;&#732;stderrâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
scripts/basic/fixdep.c:282: warning: implicit declaration of function â&#8364;&#732;fstatâ&#8364;&#8482;
scripts/basic/fixdep.c:284: warning: implicit declaration of function â&#8364;&#732;closeâ&#8364;&#8482;
scripts/basic/fixdep.c:287: warning: implicit declaration of function â&#8364;&#732;mmapâ&#8364;&#8482;
scripts/basic/fixdep.c:287: error: â&#8364;&#732;PROT_READâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: â&#8364;&#732;MAP_PRIVATEâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function â&#8364;&#732;parse_config_fileâ&#8364;&#8482;
scripts/basic/fixdep.c:296: warning: implicit declaration of function â&#8364;&#732;munmapâ&#8364;&#8482;
scripts/basic/fixdep.c:272: warning: unused variable â&#8364;&#732;stâ&#8364;&#8482;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;size_tâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;parse_dep_fileâ&#8364;&#8482;:
scripts/basic/fixdep.c:304: error: â&#8364;&#732;lenâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: â&#8364;&#732;PATH_MAXâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function â&#8364;&#732;strchrâ&#8364;&#8482;
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strchrâ&#8364;&#8482;
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:310: error: â&#8364;&#732;stderrâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memcpyâ&#8364;&#8482;
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
scripts/basic/fixdep.c:306: warning: unused variable â&#8364;&#732;sâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;print_depsâ&#8364;&#8482;:
scripts/basic/fixdep.c:343: error: storage size of â&#8364;&#732;stâ&#8364;&#8482; isnâ&#8364;&#8482;t known
scripts/basic/fixdep.c:347: error: â&#8364;&#732;O_RDONLYâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:349: error: â&#8364;&#732;stderrâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:359: error: â&#8364;&#732;PROT_READâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: â&#8364;&#732;MAP_PRIVATEâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function â&#8364;&#732;parse_dep_fileâ&#8364;&#8482;
scripts/basic/fixdep.c:343: warning: unused variable â&#8364;&#732;stâ&#8364;&#8482;
scripts/basic/fixdep.c: In function â&#8364;&#732;trapsâ&#8364;&#8482;:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
scripts/basic/fixdep.c:378: error: â&#8364;&#732;stderrâ&#8364;&#8482; undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
rob@rob-laptop:~/linux-2.6.22.14$ 


---

### Post by stratofarmer on 2009-02-23
Hi I'm using Intrepid Ibex and I ran into this issue with my Asus laptop having a SiS191 Gigabit Ethernet card.
I installed the kernel from Jaunty which solved the issue for me. Kernel version 2.6.28-8 to be precise.

Even then there's still a bug in the sis190 driver itself, it needs a workaround to work properly by setting the MTU to 1024. Don't know exactly why but it works for me.

P.S. Incidently, it also fixed the atheros wireless connection.

---

### Post by feuergeist on 2010-10-25
I had a similar problem. I had installed 9.10 freshly. On clicking the network manager icon and selecting "eth0", it would try for about 5 mins and then give up.

So I opened /etc/network/interfaces to see if eth0 had been configured. Found the eth0 entry missing. So I just added:

auto eth0
iface eth0 inet dhcp

and it started working.

---

