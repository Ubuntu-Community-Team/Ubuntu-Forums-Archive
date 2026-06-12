---
title: "Linux doesnt run on my computer..."
date: 2008-07-18
forum: General Help
---

### Post by TomPom on 2008-07-18
Hey all,
About 3 months ago i tried a few linux distro's via live CD's and usb etc, and i thought instantly...
" LINUX FTW " So instantly i searched the internet for the best linux distro and came across a quiz that told me which one was best for me. Ubuntu came top. But after installing i had trouble running it for more than 20 minuites without it crashing	:-({|=	:-({|=. My computers not that slow aswell...
AMD Sempron processor 3000+
1.80 GHz, 896 mb of ram ( I have an onboard graphics card which is set to 128 MB )
And it crashes on the most simplist things like minimising firefox, or even highlighting a few items :confused: :confused: :confused:
Could someone please tell me where im going wrong or tell me how to fix this problem
Thanks :)

---

### Post by wpshooter on 2008-07-18
Before you did the installation, did you check the integrity of the Ubuntu CD by running the verification function that in found on the initial Ubuntu boot screen menu ?

---

### Post by Joshuwa on 2008-07-18
If you have the time and resources, it might be worth it to try out various live CD's to see if it exclusive to one distro or branch.

For example, you might try Ubuntu, Xubuntu, Mint, OpenSUSE, or any others.

If one works, and the other doesn't, then it might be possible to pinpoint why. 

Since all live CD's for various configurations have a vast ammount of settings that could be different, it is likely that one will work where the other failed.

---

### Post by pseudo-random on 2008-07-18
If it's crashing as in losing power and rebooting then that's not Ubuntu, thats a bad hardware configuration. Sometimes when you upgrade components without upgrading the PSU you run this risk.

---

### Post by xeth_delta on 2008-07-18
I believe a good start would be to check what hardware you are running and whether you have the correct modules/drivers for it.

Please open a terminal and post between CODE tags (the # in the posting page) the output of the following commands:
```

lshw -businfo
lshw -C video
lshw -C audio
```

What were you doing when the crashes occured, anything in particular?

---

### Post by Mgiacchetti on 2008-07-18
is it a compaq???   if so, does your motherboard have a "better than what you have now" counterpart like the two different versions of the A8m2n LA?   You may want to think about getting another setup cause these compaq's are crap.

---

### Post by TomPom on 2008-07-18
Ok i will reply to you all in one message so i dont get flamed for double+ posting

wpshooter ;
           Nope, i will do that in about 30 minuits and get back to you, but im pretty sure theres nothing wrong with the installation disk as it worked fine on a friends computer

Joshuwa ;
         I've tried many different linux distro's and the same thing has happend, they've all crashed. By crashed i mean stopped functioning which involves me rebooting the computer, VERY ANNOYING. But Xubuntu lasts MUCH longer yet doesn't have the looks and already installed programs to get me running like other distro's. In some of them they have a program which you can search and install for other programs ( Don't have a clue what its called though lol )

pseudo-random ;
               Nope, sorry if i didnt explain this in the right way. By crashing i mean everything stops working inc. the mouse. I have to reboot the computer to get it working again, but sooner or later it will crash.

xeth_delta ;
            I'll do that later and post the results. I simply cant see the reason why windows runs fine but anything else doesnt :S

Mgiacchetti ;
             It was custom built by my brother as just a homework computer for my bedroom. The motherboard is a winfast one


I have pendrivelinux on a usb, when i run that on my computer it crashes also, but when i take it into to school ( because they have this crappy ranger remote control thing that blocks every single games website that we find ) it rus VERY smooth and allows me to do whatever i desire. I just wish this would work so i could get rid of windows completley

---

### Post by CatKiller on 2008-07-18
> **TomPom said:**
> By crashing i mean everything stops working inc. the mouse. I have to reboot the computer to get it working again, but sooner or later it will crash.

As the computer boots, you'll get a brief (3 second) prompt to press Escape to enter the GRUB menu. The bottom entry in this menu should be Memtest. Run this for a long time - say, overnight.

It might not be a memory issue, in which case you can try some other troubleshooting steps, but it's a test that's straightforward and available.

---

### Post by TomPom on 2008-07-18
Ok, ill try that tonight an get back to you all, and to the ones who i've said i will get back to them tonight, sorry, i will deffinatley try your suggestions tomorow when i wake up.

---

### Post by coffeecat on 2008-07-18
**TomPom**, if all the Linux distros you've tried crash, then that's a hardware fault - 99% certain. I'd agree with what the previous poster is suggesting. This is almost certainly a memory fault. Linux and Windows handle memory differently, so that Linux is much more likely to highlight a memory problem. Trouble is, sometimes even bad memory passes the memtest. Have you got some other memory sticks you could try in that computer.

---

### Post by cacycleworks on 2008-07-18
Your problem sounds quite similar to my [Dell C521s]("http://ubuntuforums.org/showthread.php?t=493340"). The fix for me is to run usb keyboards thru a powered hub. Maybe try that? I suspect it could be your HID human input device and your motherboard. :)

The c521 came with any of a few cpu's, 2 of mine are just the 64bit cpu, and the other 2 are the dual core X2. One of them, we upgraded the cpu to the best available and with 4G of RAM. It kinda flies now. :)

Here's the lspci from one of my Dells:
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:09.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)

```

And then the lshw commands:
```

$ lshw -businfo
WARNING: you should run this program as super-user.
Bus info          Device  Class       Description
=================================================
                          system      Computer
                          bus         Motherboard
                          memory      958MB System memory
cpu@0                     processor   AMD Athlon(tm) 64 Processor 3200+
pci@0000:00:00.0          memory      C51 Host Bridge
pci@0000:00:00.1          memory      C51 Memory Controller 0
pci@0000:00:00.2          memory      C51 Memory Controller 1
pci@0000:00:00.3          memory      C51 Memory Controller 5
pci@0000:00:00.4          memory      C51 Memory Controller 4
pci@0000:00:00.5          memory      C51 Host Bridge
pci@0000:00:00.6          memory      C51 Memory Controller 3
pci@0000:00:00.7          memory      C51 Memory Controller 2
pci@0000:00:02.0          bridge      C51 PCI Express Bridge
pci@0000:00:03.0          bridge      C51 PCI Express Bridge
[ snip -- sudo output is better ]
$
$
$ sudo lshw -businfo
[sudo] password for chris:
Bus info          Device     Class       Description
====================================================
                             system      Dimension C521
                             bus         0FP406
                             memory      128KB BIOS
cpu@0                        processor   AMD Athlon(tm) 64 Processor 3200+
                             memory      128KB L1 cache
                             memory      512KB L2 cache
                             memory      1GB System Memory
                             memory      DIMM Synchronous [empty]
                             memory      DIMM Synchronous [empty]
                             memory      512MB HYMP564U64BP8-Y5
                             memory      512MB NT512T64U88B0BY-3C
pci@0000:00:00.0             memory      C51 Host Bridge
pci@0000:00:00.1             memory      C51 Memory Controller 0
pci@0000:00:00.2             memory      C51 Memory Controller 1
pci@0000:00:00.3             memory      C51 Memory Controller 5
pci@0000:00:00.4             memory      C51 Memory Controller 4
pci@0000:00:00.5             memory      C51 Host Bridge
pci@0000:00:00.6             memory      C51 Memory Controller 3
pci@0000:00:00.7             memory      C51 Memory Controller 2
pci@0000:00:02.0             bridge      C51 PCI Express Bridge
pci@0000:00:03.0             bridge      C51 PCI Express Bridge
pci@0000:00:04.0             bridge      C51 PCI Express Bridge
pci@0000:00:05.0             display     C51 [GeForce 6150 LE]
pci@0000:00:09.0             memory      MCP51 Host Bridge
pci@0000:00:0a.0             bridge      MCP51 LPC Bridge
pci@0000:00:0a.1             bus         MCP51 SMBus
pci@0000:00:0a.2             memory      MCP51 Memory Controller 0
pci@0000:00:0b.0             bus         MCP51 USB Controller
pci@0000:00:0b.1             bus         MCP51 USB Controller
pci@0000:00:0e.0  scsi0      storage     MCP51 Serial ATA Controller
scsi@0:0.0.0      /dev/sda   disk        76GB Maxtor 6V080E0
scsi@0:0.0.0,1    /dev/sda1  volume      73GB Linux filesystem partition
scsi@0:0.0.0,2    /dev/sda2  volume      2745MB Extended partition
                  /dev/sda5  volume      2745MB Linux swap / Solaris partition
scsi@1:0.0.0      /dev/sdb   disk        232GB ST3250624AS
scsi@1:0.0.0,1    /dev/sdb1  volume      232GB Linux filesystem partition
pci@0000:00:0f.0             storage     MCP51 Serial ATA Controller
pci@0000:00:10.0             bridge      MCP51 PCI Bridge
pci@0000:04:07.0  eth0       network     BCM4401-B0 100Base-TX
pci@0000:04:09.0  eth1       network     82541PI Gigabit Ethernet Controller
pci@0000:00:10.1             multimedia  MCP51 High Definition Audio
pci@0000:00:18.0             bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration
pci@0000:00:18.1             bridge      K8 [Athlon64/Opteron] Address Map
pci@0000:00:18.2             bridge      K8 [Athlon64/Opteron] DRAM Controller
pci@0000:00:18.3             bridge      K8 [Athlon64/Opteron] Miscellaneous Control
$
$
$ sudo lshw -C video
  *-display
       description: VGA compatible controller
       product: C51 [GeForce 6150 LE]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga bus_master cap_list
       configuration: latency=0
$
$ sudo lshw -C audio
$
$

```

There is no audio on this computer -- it's a server, so "got me" on that. I know the video works, as we had one or two of them as workstations for a while.

@xeth_delta - I'd appreciate any of your thoughts on my lshw output if anything is peculiar.

Hope this helps,

:) Chris

---

### Post by cacycleworks on 2008-07-18
> **coffeecat said:**
> **TomPom**, if all the Linux distros you've tried crash, then that's a hardware fault - 99% certain. I'd agree with what the previous poster is suggesting. This is almost certainly a memory fault. Linux and Windows handle memory differently, so that Linux is much more likely to highlight a memory problem. Trouble is, sometimes even bad memory passes the memtest. Have you got some other memory sticks you could try in that computer.

Upon rereading this thread, I just realized that we had the same issues on the c521 in SLAX, knoppix, and Ubuntu.

:) Chris

---

### Post by hansdown on 2008-07-18
Hi tompom. A while back I was running a compaq with the same sempron processor. I was using xp and ie, which allowed serious bugs onto my computer, one of which was a win32 bug that eventually fried my cpu. By the time I got smart and switched to ubuntu, I could't run any os without serious freezing.

---

### Post by cacycleworks on 2008-07-18
> **hansdown said:**
> Hi tompom. A while back I was running a compaq with the same sempron processor. I was using xp and ie, which allowed serious bugs onto my computer, one of which was a [COLOR="Red"]win32 bug that eventually fried my cpu[/COLOR]. By the time I got smart and switched to ubuntu, I could't run any os without serious freezing.

What? OMG, I never knew it could do that! Ay carumba! 

If so, go get a better 64X2 ;) [newegg has my new one for $87]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103235") and a 4400 for $58. 

Hmmm, looks like it's got 8G, not 4:
```

$ sudo lshw -businfo
[sudo] password for chris:
Bus info          Device      Class       Description
=====================================================
                              system      Dimension C521
                              bus         0FP406
                              memory      128KB BIOS
cpu@0                         processor   AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
                              memory      128KB L1 cache
                              memory      2MB L2 cache
                              memory      4GB System Memory
                              memory      DIMM Synchronous [empty]
                              memory      2GB PDC24G6400ELK
                              memory      DIMM Synchronous [empty]
                              memory      2GB PDC24G6400ELK

```

---

### Post by TomPom on 2008-07-19
[FONT="Tahoma"]> **coffeecat said:**
> **TomPom**, if all the Linux distros you've tried crash, then that's a hardware fault - 99% certain. I'd agree with what the previous poster is suggesting. This is almost certainly a memory fault. Linux and Windows handle memory differently, so that Linux is much more likely to highlight a memory problem. Trouble is, sometimes even bad memory passes the memtest. Have you got some other memory sticks you could try in that computer.

Tried the memtest over night, and 22 passes with no fails

Here is the lshw -businfo results
Bus info          Device      Class       Description
=====================================================
                              system      Computer
                              bus         Motherboard
                              memory      894MiB System memory
cpu@0                         processor   AMD Sempron(tm) Processor 3000+
                              memory      128KiB L1 cache
                              memory      128KiB L2 cache
pci@0000:00:00.0              bridge      760/M760 Host
pci@0000:00:01.0              bridge      SG86C202
pci@0000:01:00.0              display     661/741/760 PCI/AGP or 662/761Gx PCIE 
pci@0000:00:02.0              bridge      SiS964 [MuTIOL Media IO]
pci@0000:00:02.5  scsi0       storage     5513 [IDE]
scsi@0:0.0.0      /dev/cdrom  disk        DVD_RW ND-3500AG
                  /dev/cdrom  disk        
pci@0000:00:02.7              multimedia  AC'97 Sound Controller
pci@0000:00:03.0              bus         USB 1.1 Controller
pci@0000:00:03.1              bus         USB 1.1 Controller
pci@0000:00:03.2              bus         USB 1.1 Controller
pci@0000:00:03.3              bus         USB 2.0 Controller
pci@0000:00:04.0  eth0        network     SiS900 PCI Fast Ethernet
pci@0000:00:05.0              storage     RAID bus controller 180 SATA/PATA  [Si
pci@0000:00:07.0              bridge      RL5c475
pci@0000:00:18.0              bridge      K8 [Athlon64/Opteron] HyperTransport T
pci@0000:00:18.1              bridge      K8 [Athlon64/Opteron] Address Map
pci@0000:00:18.2              bridge      K8 [Athlon64/Opteron] DRAM Controller
pci@0000:00:18.3              bridge      K8 [Athlon64/Opteron] Miscellaneous Co
pci@0000:02:00.0              network     AGN100 802.11 a/b/g True MIMO Wireless

lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller cap_list
       configuration: latency=0

lshw -C audio
WARNING: you should run this program as super-user.
ubuntu@ubuntu:~$      

I'll have to ask my mom about that cpu as im only 14:lolflag: I doubt very much she will, but i get 150 ( GBP ) for my birthday in september. Tbh i want a simple fix without havin to spend money. BUt if it comes down to spending money i guess ill have too:D

And P.S, When i install windows xp, the first thing i go onto is firefox. Never use IE[/FONT]

---

### Post by wpshooter on 2008-07-19
Tompom:

Some things to try.

Have you checked to make sure that your BIOS is on the latest and greatest version ?

Have you checked to make sure that your CD-Rom firmware is on the latest and greatest version ?

What video card are you using and how are you going about installing any video card drivers, if any ?  My guess would be that your problem probably lays in the video card driver area.  If you are installing any type of video drivers (other than what is being installed by the O/S installation by default) then try reinstalling the O/S and DON'T changed the video setup from the default for a while and see if you have any freezing problems running in that mode before you attempt to install any outside video card drivers.

---

