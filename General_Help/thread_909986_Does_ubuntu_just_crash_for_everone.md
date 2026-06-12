---
title: "Does ubuntu just crash for everone?"
date: 2008-09-04
forum: General Help
---

### Post by peterbug on 2008-09-04
ok for the past year or so I have been plagued with my ubuntu desktop crashing randomly, the whole system seized up and the caps button would flash, the only way to restore it was to turn it off and back on and it would happen at any given time be start up or half way through writing up course work on my computer to playing a game. I assumed it was a hardware problem because my computer wasn't so up to date.

however I have just bought a completely new computer assuming that this would solve all my problems with crashing and hoping I could wave good by to ever seeing that flashing caps lock button for good. however it was not to be so far it has done the exact same thing 3 times since I have had my new computer. the only thing that has remained is my monitor subwoofer and speakers. 

Do all ubuntu desktops have this problem or is it unique to mine? if so how can it possibly happen to me? it must be software side...right?

can anyone offer up a suggestion?

p.s

my new computers specs are as follows :

Processor Type - Intel Core 2 Duo Processor E4500  	 
RAM Memory - 2048 MB 	 
Hard Disk Capacity - 250 GB 	 
Graphics Card - nVidia GeForce 8400 GS

---

### Post by Rainstride on 2008-09-04
no thats not normal... did you use the same copy to install ubuntu?

---

### Post by iaculallad on 2008-09-04
Eversince the first installation of Hardy (and now upgraded to 8.04.1) on my Aspire notebook and Gutsy on my Desktop (with similar specs as yours but with Intel D E2180 2.0Ghz), So far so good.
EDIT: Try downloading a fresh new 8.04.1 ISO and try installing it again on your unit.

---

### Post by peterbug on 2008-09-04
on this occassion I did yes, however I have had the same problem from 6.10 and am now all the way up to 8.4 so I doubt it is the disk I'm using to install it because that has changed over time.

ok dudes I'm gona download a new cd and burn in and try it out though I can't see why it should make a difference after the mount of cds I have gone through in the past =P but its worth a try

---

### Post by Rainstride on 2008-09-04
> **peterbug said:**
> on this occassion I did yes, however I have had the same problem from 6.10 and am now all the way up to 8.4 so I doubt it is the disk I'm using to install it because that has changed over time.

i really dont see it being a hardware problem.... it could be a bad disk from your old burner failing. my dvd burner was messed up and i didn't notice it was causing burn errors. try burning a fresh copy with your new computer and integrity test on the disk to be sure it burned right.

and then fresh install, it should work fine after that. it cant be your hardware if its happening on a new comp. has to be software.

---

### Post by peterbug on 2008-09-04
haha! it just did it again half way through the download haha!

thanks for taking time to help me guys, I'll try again now =P

---

### Post by Rainstride on 2008-09-04
no problem. 
if it does it to much to download the iso, try the bittorrent files. it will atleast keep most of the file if you get knocked off, and you can pick up where you were.

you might also want to use a CD-RW just in case you lock up in mid-burn. that way you wont waste a cd.

---

### Post by Kevbert on 2008-09-04
No crashes here.
It may be worth running a memory check on both computers.  You can do this from the grub boot screen or the CD boot screen.  Leave it to run for two or three passes.  You should not get any errors.  If the new PC does it then it may be due to poorly seated ram.  In the case of the old PC, it could be due to a build-up of dust.

---

### Post by Kinetic_lord on 2008-09-04
What have you installed on you're Ubuntu? it must be because of some application or something... :confused: or maybe the graphics card???

---

### Post by mixmaster on 2008-09-04
I have to say that I run Ubuntu on several different machines and I can't remember the last time I had a crash/lockup except those associated with screensavers under Dapper.

I would look at something else common between the old and new systems - do you have any software which doesn't come from a reputable repository, particularly anything you have built yourself?  Or any proprietory hardware drivers?

---

### Post by Dark Hornet on 2008-09-04
I would have to agree with Mixmaster...it sounds like it might be a problem with a software package or repository that is common between both systems.  I have been running Ubuntu for a few years now, and have never had this issue...Good luck!

Darkhornet

---

### Post by jespdj on 2008-09-04
No, Ubuntu does not just crash for everyone; if it would be so unstable, then it would not be so popular. I have been running Ubuntu on a number of different computers the past two years and I've never seen it lock up completely.

You most likely have a problem with a buggy driver, or maybe even faulty hardware. Try running the memory test program: reboot, and in the GRUB menu choose "memtest86+". Let the memory test run for a few hours and see if it finds any errors. If it does, then there's a hardware problem with the memory in your computer.

---

### Post by peterbug on 2008-09-04
ok I downloaded and burnt a new copy of ubuntu 8.4 then I check the disk to make sure it was ok, after that I checked the memory to make sure that was all in order, but as expected came up as all clear then I installed my new version of ubuntu and set everything just, just as I had finished setting it all up boom! it crashed again. I don't even know how or why this is possible, here is a list of what I did when setting up:

1) I updated my system fully using the provided update manager

2) I installed the restricted driver for my graphics card

3) I installed the compiz effects manager and screen lets from the ubuntu repo

4) I installed the restrictedfromants from ubuntu using ```
sudo apt-get install ubuntu-restricted-extras
```

5) rebooted my system 

6) my computer crashed again, complete seeze up nothing would work at all other than turning it off and back on again.

any ideas at all why this might be happening to me?

---

### Post by Dougie187 on 2008-09-04
Can you post the output of dmesg? Only do it after a freeze though.

---

### Post by peterbug on 2008-09-04
nothing responds after a freeze how can I give you that read out if the system is locked up?

---

### Post by HermanAB on 2008-09-04
First off - any kind of Linux should be able to run for several years without failure and without updates and restarts.

# uptime
 14:13:33 up 241 days, 10:50,  1 user,  load average: 0.32, 0.72, 0.48

If your system is unstable across various versions of Linux then it has to be related to either a bad power supply (install a UPS for maximum life of your machine) or a bad driver that you always install for a specific anciliary device (scanner, camera, modem...)

I suspect that you have a power quality problem and that spikes are killing your system.  I'd recommend that you invest in a UPS.

Cheers,

Herman

---

### Post by peterbug on 2008-09-04
I doubt its a power supply problem the same problem has been presant while I was living at home, while I was in student halls and now where I am in my new flat...

however if you think a faulty driver or something along those lines is to blame the only thing I can think off would be my webcam, I think other than my monitor that is the only hardware that has been presant as long as my freezing problems...

how could I investigate this further?

---

### Post by Scrotnig on 2008-09-04
Mine never crashes, but then I have hardly ever had Windows XP crash either, on a different machine.

Maybe I'm just lucky.

---

### Post by llebegue on 2008-09-04
You will find in this thread that you are not alone ;)

[http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510)

---

### Post by peterbug on 2008-09-04
so your saying that maybe it has nothing at all to do with my drivers or anything like that, rather its just that my old computer was messed up so it crashed and now hardy is kinda buggy so its been crashing for people to so maybe I'm just unlucky? I guess I'll have to try another distro out then.

if anyone has any other ideas though please let me know!

---

### Post by Dark Hornet on 2008-09-04
I am not saying that this is the issue, but...just throwing it out there....are you sure that your CPU/hardware is not overheating?  I know that in the past and currently (not that I have personally dealt with these issues--but I have read a little about them) but I have heard that with some motherboards, Linux does not play nice -- as in control--the CPU fan/heat sync very well.  Personally I use liquid to cool my CPU, so I don't run into this issue, but I am pretty sure I remember reading about this a while ago...

Darkhornet

---

### Post by Rainstride on 2008-09-04
> **peterbug said:**
> I doubt its a power supply problem the same problem has been presant while I was living at home, while I was in student halls and now where I am in my new flat...

however if you think a faulty driver or something along those lines is to blame the only thing I can think off would be my webcam, I think other than my monitor that is the only hardware that has been presant as long as my freezing problems...

how could I investigate this further?

the chances of this happening on 2 different computers with 2 different install disks and no common hardware is pretty small. there has to be some common thing between both computers thats causing this. 
try not using any of your old hardware (keyboard, mouse, webcam) except your monitor (unless you have a new one). 
chances are if you carry over hardware from your old computer to the new one and the crashing goes with, its the hardware from the old computer.

so i would suggest trying again with just your new hardware and see what happens. if it still happens then it could be a bug in hardy.

---

### Post by pbhj on 2008-09-04
> **Rainstride said:**
> the chances of this happening on 2 different computers with 2 different install disks and no common hardware is pretty small. there has to be some common thing between both computers thats causing this.

Well I'd say he could of been putting computer in the same place, then that would have been a common point between old and new computers. He says he's had the computer since at home, then at college and now in his flat ... assuming 3 year Uni, then that's going to be about 5 years old ... but this is supposed to be a new computer??

I'm with Dr.House on this one ... something is not straight, I don't think you're telling it to us as it us but as you think you should to get the answer you want? Sorry.

**In summary**, 2 computers, from versions 6 to 8.04 of Ubuntu, no non-perpipheral hardware (RAM, hdd, powerstrip, PSU, CDROM, nothing) in common, no location in common, no non-standard software in common. Only common point for failure then is monitor, speakers, webcam, (keyboard and mouse?), you ....

You can run it without neither webcam, speakers, not monitor and see if it crashes (that would rule them out). You can alter bios to run it without the keyboard (just mouse, but plug back in the monitor so you can tell if it's working). If neither of those scenarios work then you've to start removing things from your mobo. Begin with CD/DVD, and network or audio cards and any extra memory. You should just have PSU, Mobo, one RAM stick, one HDD in the tower. Plug computer into it's own power socket (on it's own ring if you can), use an extension cable for monitor.

I'd also try a different OS if you have one (even just a bootable utility or just boot to the GrUB prompt and leave it there; there's a boot from CD version of MS Windows, "Barts" I think it's called or there are MSDOS versions to boot to on things like UBCD) or something very basic like TomsRtBt which should rule out a software problem.

Incidentally someone mentioned a problem with hardy and one of the 2.6 kernels, this couldn't have caused problems for the last 5-10 years,.

As someone said this looks like a power supply issue, either mains or PSU, it could be caused by an old CRT they can kick out huge voltages, if that's interfering with the supply that could be your source.

Are you familiar with using Ctrl-Alt-F1 to get a console (when graphics driver crashes) and with using Alt-SysRq-* combinations?

---

### Post by peterbug on 2008-09-05
pbhj you are assuming quite alot which is why I think you don't understand the change between two computers,I'm only going into my second year of university now. I was in my first year with my computer in uni with me and I had it at home running linux for a year prior to that so it was only 2 years old. I have now moved in to a new flat and bought an entirely new computer in a bid to stop these crashes. the computer I am running now is about a week old. 

I tried running mint linux (I know its based on ubuntu) and the crash happened again. I'm gona download something red hat based and see what that does. if it crashes yet again, which I fully expect it to. I'll start stripping down my peripherals.

however is it likely that my grphics card could be to blame? (NVIDIA® GeForce® 8400)

---

### Post by beniwtv on 2008-09-05
Just for information (because nobody else mentioned):

Caps lock flashing (or all leds simultaneously on your keyboard) is a so called "Kernel oops". Means that something has gone terribly wrong and the kernel has crashed.

Unfortunately, this can have various causes, as mentioned by this thread. 

I had the same problem (Ubuntu crashing on various versions), but in my case it was the WiFi card. I had installed NDISWrapper because the Ubuntu drivers didn't work (blame Broadcom for that), and apparently NDISWrapper and NVIDIA don't like each other.

When 8.04 came along, Ubuntu's drivers worked OOTB and the crashes were gone.

Maybe it could be a similar thing on your end, some driver of some obscure hardware in combination of another device you have that causes the kernel to crash.

Cheers,

---

### Post by peterbug on 2008-09-05
thanks I did wonder what that meant...

well I removed my webcam and replaced my wireless mouse and did a fresh install of ubuntu and on first boot it crashed. so I think its safe to say I can rule out my webcam or mouse being the problem, I've replaced my keyboard now and am going to go out and buy a different wifi usb adapter and see where I go from there.

---

### Post by Rainstride on 2008-09-05
> **peterbug said:**
> thanks I did wonder what that meant...

well I removed my webcam and replaced my wireless mouse and did a fresh install of ubuntu and on first boot it crashed. so I think its safe to say I can rule out my webcam or mouse being the problem, I've replaced my keyboard now and am going to go out and buy a different wifi usb adapter and see where I go from there.

hmm... you should have just tried it with just your mouse and key board at first(helps find the cause of the problem). if there is no crash with nothing but bare min plugged in and it crashes with everything plugged in its safe to say it is one of those peaces of hardware. also it saves money to find the exact problem first:).

i know sometimes faulty hardware or bad plugs can cause hard locks.

---

### Post by Dougie187 on 2008-09-05
@peterbug
When i asked for a copy of dmesg i meant after you boot back up, but only after you had a lockup. So for instance, Don't do it if you had just rebooted your computer sucessfully. These logs store information for a little bit of time, so if you had some kernel error or hardware error that the system picks up it will be in the log when you turn it back on after a lockup. So if you post these logs, maybe one of us can help determine what is causing the lockups.

Also, if you are considering getting a new wifi adapter, I would suggest getting a pci one instead of a usb one, since I have heard more issues with the usb then the pci.

---

### Post by Crafty Kisses on 2008-09-05
Not for me, it could be a lot of issues, resource issues, RAM issues, bad HD's. It just depends.

---

### Post by Threbus5 on 2008-09-05
Well, no, Ubuntu seems extraordinarily stable.
How do the computers behave with a different OS installed?
How about some of the other Linux based OS's or even a Windows install?
It might be worth the $15 or $20 for an old Windows OS to verify system integrity.
Ubuntu 6.06 is about a solid as a granite wall and if that crashed it is most likely a non OS issue.

---

### Post by revanb on 2008-09-05
I am having some lock ups as well. I suspect it is to do with the graphics driver. I have only today found out about the "envy" program which installs and sets up the correct graphics driver apparently.  So I'm gonna tyr it.

I am guessing it must be a driver, because isn't linux supposed to be stable when it comes to software only. ie You should be able to kill hanging software. Only with drivers which deal with hardware the linux kernel (or any OS) can't do anything if the driver messes up the hardware.

---

### Post by peterbug on 2008-09-05
ok I went out and bought a new wifi adapter I stuck with a usb one and reinstalled ubuntu and have set everything up. since then I have rebooted several times and installed my nvidia driver etc. so far I have had no system lock ups and everything is running smoothly.

I'm gona wait a week before I mark this post as solved just incase something comes up but I doubt it will, I think its reasonable to assume that the problem was my wifi driver and that it was total coincidence that my previous desktop crashed also (I used an ethernet cable not a wifi adapter on that box) so I guess I was just unlucky. thanks to everyone that helped me and I hope that I'll be back in a week to mark this as solved.

---

### Post by peterbug on 2008-09-05
I just froze =[

I took a dmesg just after I rebooted this time though;

```
000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519907
[    0.000000] Kernel command line: root=UUID=489ecafb-6d3c-4cf6-95e0-3d5f7026ac52 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.239 MHz processor.
[   20.090121] Console: colour VGA+ 80x25
[   20.090125] console [tty0] enabled
[   20.090402] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.090659] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.167732] Memory: 2065688k/2096000k available (2177k kernel code, 29088k reserved, 1006k data, 368k init, 1178496k highmem)
[   20.167738] virtual kernel memory layout:
[   20.167739]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.167740]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.167741]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.167742]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.167742]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.167743]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   20.167744]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   20.167747] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.167806] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.167939] hpet clockevent registered
[   20.247862] Calibrating delay using timer specific routine.. 4402.75 BogoMIPS (lpj=8805510)
[   20.247888] Security Framework initialized
[   20.247898] SELinux:  Disabled at boot.
[   20.247917] AppArmor: AppArmor initialized
[   20.247921] Failure registering capabilities with primary security module.
[   20.247928] Mount-cache hash table entries: 512
[   20.248074] Initializing cgroup subsys ns
[   20.248080] Initializing cgroup subsys cpuacct
[   20.248092] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   20.248098] monitor/mwait feature present.
[   20.248099] using mwait in idle threads.
[   20.248103] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.248105] CPU: L2 cache: 2048K
[   20.248108] CPU: Physical Processor ID: 0
[   20.248109] CPU: Processor Core ID: 0
[   20.248111] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   20.248119] Compat vDSO mapped to ffffe000.
[   20.248133] Checking 'hlt' instruction... OK.
[   20.264241] SMP alternatives: switching to UP code
[   20.265612] Early unpacking initramfs... done
[   20.539573] ACPI: Core revision 20070126
[   20.539611] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.542974] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   20.542988] SMP alternatives: switching to SMP code
[   20.543579] Booting processor 1/1 eip 3000
[   20.553773] Initializing CPU#1
[   20.631476] Calibrating delay using timer specific routine.. 4399.93 BogoMIPS (lpj=8799878)
[   20.631481] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   20.631485] monitor/mwait feature present.
[   20.631488] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.631489] CPU: L2 cache: 2048K
[   20.631491] CPU: Physical Processor ID: 0
[   20.631492] CPU: Processor Core ID: 1
[   20.631493] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   20.631994] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   20.632015] Total of 2 processors activated (8802.69 BogoMIPS).
[   20.632340] ENABLING IO-APIC IRQs
[   20.632522] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.779424] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   20.799419] Brought up 2 CPUs
[   20.799436] CPU0 attaching sched-domain:
[   20.799439]  domain 0: span 03
[   20.799440]   groups: 01 02
[   20.799443] CPU1 attaching sched-domain:
[   20.799444]  domain 0: span 03
[   20.799445]   groups: 02 01
[   20.799621] net_namespace: 64 bytes
[   20.799629] Booting paravirtualized kernel on bare hardware
[   20.800013] Time: 21:01:53  Date: 09/05/08
[   20.800035] NET: Registered protocol family 16
[   20.800174] EISA bus registered
[   20.800178] ACPI: bus type pci registered
[   20.807443] PCI: PCI BIOS revision 3.00 entry at 0xfa760, last bus=128
[   20.807444] PCI: Using configuration type 1
[   20.807456] Setting up standard PCI resources
[   20.808400] mtrr: your CPUs had inconsistent fixed MTRR settings
[   20.808401] mtrr: probably your BIOS does not setup all CPUs.
[   20.808403] mtrr: corrected configuration.
[   20.809983] ACPI: EC: Look up EC in DSDT
[   20.815951] ACPI: Interpreter enabled
[   20.815953] ACPI: (supports S0 S3 S4 S5)
[   20.815964] ACPI: Using IOAPIC for interrupt routing
[   20.821597] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.823128] PCI: Transparent bridge - 0000:00:13.1
[   20.823160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.823343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[   20.823433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   20.823519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[   20.848464] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   20.848581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   20.848971] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[   20.849104] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   20.849238] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[   20.849372] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 6 7 10 11 12)
[   20.849497] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 *7 10 11 12)
[   20.849619] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0
[   20.849733] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   20.849854] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[   20.849973] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.849994] pnp: PnP ACPI init
[   20.850000] ACPI: bus type pnp registered
[   20.853214] pnp: PnP ACPI: found 15 devices
[   20.853215] ACPI: ACPI bus type pnp unregistered
[   20.853219] PnPBIOS: Disabled by ACPI PNP
[   20.853375] PCI: Using ACPI for IRQ routing
[   20.853377] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.802370] NET: Registered protocol family 8
[   21.802373] NET: Registered protocol family 20
[   21.802414] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[   21.802420] hpet0: 3 32-bit timers, 14318180 Hz
[   21.803449] AppArmor: AppArmor Filesystem Enabled
[   21.806368] Time: tsc clocksource has been installed.
[   21.806378] Switched to high resolution mode on CPU 0
[   21.806472] Switched to high resolution mode on CPU 1
[   21.822383] system 00:01: ioport range 0x400-0x47f has been reserved
[   21.822387] system 00:01: ioport range 0x500-0x50f has been reserved
[   21.822395] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   21.822399] system 00:02: ioport range 0x800-0x805 has been reserved
[   21.822402] system 00:02: ioport range 0x290-0x297 has been reserved
[   21.822406] system 00:02: ioport range 0x880-0x88f has been reserved
[   21.822419] system 00:09: iomem range 0xf0001000-0xf0001fff has been reserved
[   21.822427] system 00:0a: iomem range 0xf0002000-0xf0002fff has been reserved
[   21.822434] system 00:0b: iomem range 0xf0000000-0xf0000fff has been reserved
[   21.822442] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.822451] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
[   21.822455] system 00:0e: iomem range 0xfe800000-0xfe8000ff has been reserved
[   21.822459] system 00:0e: iomem range 0x7fee0000-0x7fefffff could not be reserved
[   21.822463] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   21.822467] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   21.822471] system 00:0e: iomem range 0x100000-0x7fedffff could not be reserved
[   21.822475] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[   21.822479] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.822483] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
[   21.852778] PCI: Bridge: 0000:00:01.0
[   21.852781]   IO window: b000-bfff
[   21.852785]   MEM window: dfb00000-dfbfffff
[   21.852788]   PREFETCH window: dfe00000-dfefffff
[   21.852794] PCI: Bridge: 0000:00:02.0
[   21.852796]   IO window: a000-afff
[   21.852800]   MEM window: da000000-ddffffff
[   21.852803]   PREFETCH window: c0000000-cfffffff
[   21.852807] PCI: Bridge: 0000:00:03.0
[   21.852809]   IO window: c000-cfff
[   21.852814]   MEM window: dfd00000-dfdfffff
[   21.852818]   PREFETCH window: dfc00000-dfcfffff
[   21.852823] PCI: Bridge: 0000:00:13.1
[   21.852825]   IO window: 9000-9fff
[   21.852829]   MEM window: dfa00000-dfafffff
[   21.852832]   PREFETCH window: df900000-df9fffff
[   21.852847] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.852862] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
[   21.852867] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.852882] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
[   21.852886] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   21.852898] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   21.852906] NET: Registered protocol family 2
[   21.890347] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.890555] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.891073] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.891397] TCP: Hash tables configured (established 131072 bind 65536)
[   21.891399] TCP reno registered
[   21.902440] checking if image is initramfs... it is
[   22.441087] Freeing initrd memory: 7705k freed
[   22.441831] audit: initializing netlink socket (disabled)
[   22.441851] audit(1220648513.325:1): initialized
[   22.442049] highmem bounce pool size: 64 pages
[   22.443534] VFS: Disk quotas dquot_6.5.1
[   22.443592] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.443719] io scheduler noop registered
[   22.443720] io scheduler anticipatory registered
[   22.443722] io scheduler deadline registered
[   22.443730] io scheduler cfq registered (default)
[   22.443745] PCI: VIA PCI bridge detected. Disabling DAC.
[   22.443835] Boot video device is 0000:02:00.0
[   22.443937] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.443976] assign_interrupt_mode Found MSI capability
[   22.444024] Allocate Port Service[0000:00:02.0:pcie00]
[   22.444049] Allocate Port Service[0000:00:02.0:pcie02]
[   22.444122] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   22.444168] assign_interrupt_mode Found MSI capability
[   22.444218] Allocate Port Service[0000:00:03.0:pcie00]
[   22.444241] Allocate Port Service[0000:00:03.0:pcie02]
[   22.444443] isapnp: Scanning for PnP cards...
[   22.798208] isapnp: No Plug & Play device found
[   22.816928] Real Time Clock Driver v1.12ac
[   22.817104] hpet_resources: 0xfe800000 is busy
[   22.817155] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.818088] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.818143] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.818217] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   22.818219] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   22.818313] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.831044] mice: PS/2 mouse device common for all mice
[   22.831128] EISA: Probing bus 0 at eisa.0
[   22.831165] EISA: Detected 0 cards.
[   22.831169] cpuidle: using governor ladder
[   22.831170] cpuidle: using governor menu
[   22.831254] NET: Registered protocol family 1
[   22.831282] Using IPI No-Shortcut mode
[   22.831312] registered taskstats version 1
[   22.831408]   Magic number: 8:582:44
[   22.831411]   hash matches device ttyed
[   22.831501] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.831503] EDD information not available.
[   22.831683] Freeing unused kernel memory: 368k freed
[   22.854078] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.032318] fuse init (API version 7.9)
[   24.060028] ACPI: SSDT 7FEE9D00, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   24.060189] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.060198] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.328673] SCSI subsystem initialized
[   24.334323] libata version 3.00 loaded.
[   24.335673] sata_via 0000:00:0f.0: version 2.3
[   24.335702] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18
[   24.335731] sata_via 0000:00:0f.0: routed to hard irq line 11
[   24.335782] scsi0 : sata_via
[   24.335820] scsi1 : sata_via
[   24.336827] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 18
[   24.336829] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 18
[   24.351519] usbcore: registered new interface driver usbfs
[   24.351537] usbcore: registered new interface driver hub
[   24.351556] usbcore: registered new device driver usb
[   24.352395] USB Universal Host Controller Interface driver v3.0
[   24.425991] 8139too Fast Ethernet driver 0.9.28
[   24.539832] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.700976] ata1.00: ATA-7: Hitachi HDT725025VLA380, V5DOA7BA, max UDMA/133
[   24.700980] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.716881] ata1.00: configured for UDMA/133
[   24.919490] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   24.930529] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5
[   24.930765] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 19
[   24.930776] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   24.931072] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   24.931095] uhci_hcd 0000:00:10.0: irq 19, io base 0x0000e000
[   24.931211] usb usb1: configuration #1 chosen from 1 choice
[   24.931230] hub 1-0:1.0: USB hub found
[   24.931234] hub 1-0:1.0: 2 ports detected
[   25.031516] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 20
[   25.031528] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   25.031563] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   25.031583] uhci_hcd 0000:00:10.1: irq 20, io base 0x0000dc00
[   25.031670] usb usb2: configuration #1 chosen from 1 choice
[   25.031687] hub 2-0:1.0: USB hub found
[   25.031691] hub 2-0:1.0: 2 ports detected
[   25.135403] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   25.135413] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   25.135441] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   25.135467] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d800
[   25.135554] usb usb3: configuration #1 chosen from 1 choice
[   25.135571] hub 3-0:1.0: USB hub found
[   25.135575] hub 3-0:1.0: 2 ports detected
[   25.239287] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21
[   25.239297] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   25.239325] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   25.239354] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[   25.239435] usb usb4: configuration #1 chosen from 1 choice
[   25.239452] hub 4-0:1.0: USB hub found
[   25.239455] hub 4-0:1.0: 2 ports detected
[   25.271176] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   25.343259] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 20 (level, low) -> IRQ 19
[   25.395924] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfafe000-dfafe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   25.406698] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 21 (level, low) -> IRQ 18
[   25.407214] eth0: RealTek RTL8139 at 0x9c00, 00:1c:25:30:24:dd, IRQ 18
[   25.407216] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   25.408564] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   25.408592] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[   25.408601] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   25.408628] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   25.408657] ehci_hcd 0000:00:10.4: irq 18, io mem 0xdffff000
[   25.420038] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.420185] usb usb5: configuration #1 chosen from 1 choice
[   25.420211] hub 5-0:1.0: USB hub found
[   25.420216] hub 5-0:1.0: 8 ports detected
[   25.434623] usb 1-1: device descriptor read/all, error -71
[   25.525800] pata_via 0000:00:0f.1: version 0.3.3
[   25.526255] scsi2 : pata_via
[   25.526680] scsi3 : pata_via
[   25.527618] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[   25.527621] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[   25.535949] Driver 'sd' needs updating - please use bus_type methods
[   25.536021] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.536030] sd 0:0:0:0: [sda] Write Protect is off
[   25.536032] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.536044] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.536086] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.536094] sd 0:0:0:0: [sda] Write Protect is off
[   25.536096] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.536108] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.536110]  sda: sda1 sda2 sda3 sda4
[   25.585365] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.589726] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.842984] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-H40N, RG01, max UDMA/66
[   26.014710] ata3.00: configured for UDMA/66
[   26.120204] Attempting manual resume
[   26.120206] swsusp: Resume From Partition 8:3
[   26.120208] PM: Checking swsusp image.
[   26.120348] PM: Resume from disk failed.
[   26.132382] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.132384] EXT3-fs: write access will be enabled during recovery.
[   26.173782] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H40N  RG01 PQ: 0 ANSI: 5
[   26.173883] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   26.180285] Driver 'sr' needs updating - please use bus_type methods
[   26.197612] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.197617] Uniform CD-ROM driver Revision: 3.20
[   26.197683] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   26.625985] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   26.674012] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200043a579]
[   26.896916] usb 5-1: configuration #1 chosen from 1 choice
[   27.133470] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   27.266480] usb 5-2: configuration #1 chosen from 1 choice
[   27.688924] usb 5-8: new high speed USB device using ehci_hcd and address 5
[   27.838610] usb 5-8: configuration #1 chosen from 1 choice
[   27.840074] usbcore: registered new interface driver libusual
[   27.843581] Initializing USB Mass Storage driver...
[   28.076570] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   28.258512] usb 2-1: configuration #1 chosen from 1 choice
[   28.261556] scsi4 : SCSI emulation for USB Mass Storage devices
[   28.261603] usb-storage: device found at 3
[   28.261604] usb-storage: waiting for device to settle before scanning
[   28.261623] scsi5 : SCSI emulation for USB Mass Storage devices
[   28.261665] usbcore: registered new interface driver usb-storage
[   28.261667] USB Mass Storage support registered.
[   28.261747] usb-storage: device found at 5
[   28.261749] usb-storage: waiting for device to settle before scanning
[   28.273245] usbcore: registered new interface driver hiddev
[   28.313795] input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input2
[   28.324414] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:10.1-1
[   28.324432] usbcore: registered new interface driver usbhid
[   28.324436] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.745227] kjournald starting.  Commit interval 5 seconds
[   30.745240] EXT3-fs: sda4: orphan cleanup on readonly fs
[   30.745249] ext3_orphan_cleanup: deleting unreferenced inode 622810
[   30.745296] ext3_orphan_cleanup: deleting unreferenced inode 1269794
[   30.745309] EXT3-fs: sda4: 2 orphan inodes deleted
[   30.745311] EXT3-fs: recovery complete.
[   30.776033] EXT3-fs: mounted filesystem with ordered data mode.
[   33.255864] usb-storage: device scan complete
[   33.255977] usb-storage: device scan complete
[   33.256367] scsi 4:0:0:0: Direct-Access     WD       3200AAJ External 1.06 PQ: 0 ANSI: 0
[   33.257585] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   33.258333] sd 4:0:0:0: [sdb] Write Protect is off
[   33.258336] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   33.258339] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   33.259332] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   33.259959] sd 4:0:0:0: [sdb] Write Protect is off
[   33.259962] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   33.259964] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   33.259968]  sdb:<5>scsi 5:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   33.268852] scsi 5:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   33.275471] scsi 5:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   33.282092] scsi 5:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   37.745173] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   37.820813] Linux agpgart interface v0.102
[   37.860554] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.873533] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.938229] agpgart: Detected VIA P4M890 chipset
[   37.944740] agpgart: AGP aperture is 128M @ 0xd0000000
[   38.113327] input: Power Button (FF) as /devices/virtual/input/input4
[   38.168266] ACPI: Power Button (FF) [PWRF]
[   38.168318] input: Power Button (CM) as /devices/virtual/input/input5
[   38.236185] ACPI: Power Button (CM) [PWRB]
[   38.236237] input: Sleep Button (CM) as /devices/virtual/input/input6
[   38.268167] ACPI: Sleep Button (CM) [SLPB]
[   38.426536] nvidia: module license 'NVIDIA' taints kernel.
[   38.782023] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 22
[   38.782033] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   38.782125] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   39.083979]  sdb1
[   39.084043] sd 4:0:0:0: [sdb] Attached SCSI disk
[   39.084089] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   39.085520] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   39.085552] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   39.086634] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[   39.086665] sd 5:0:0:1: Attached scsi generic sg4 type 0
[   39.087752] sd 5:0:0:2: [sde] Attached SCSI removable disk
[   39.087783] sd 5:0:0:2: Attached scsi generic sg5 type 0
[   39.088877] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[   39.088907] sd 5:0:0:3: Attached scsi generic sg6 type 0
[   39.145393] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 23
[   39.145415] PCI: Setting latency timer of device 0000:80:01.0 to 64
[   39.177109] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   39.376385] phy0: Selected rate control algorithm 'simple'
[   39.482379] usbcore: registered new interface driver rt73usb
[   39.494828] usbcore: registered new interface driver rt2500usb
[   39.802591] lp: driver loaded but no devices found
[   39.880810] Adding 9767512k swap on /dev/sda3.  Priority:-1 extents:1 across:9767512k
[   40.411848] EXT3 FS on sda4, internal journal
[   41.539211] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.900472] No dock devices found.
[   42.753958] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   42.753963] apm: disabled - APM is not SMP safe.
[   42.865665] ppdev: user-space parallel port driver
[   42.964077] audit(1220644934.247:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5235 profile="/usr/sbin/cupsd" namespace="default"
[   44.117223] eth0: link down
[   44.226342] Bluetooth: Core ver 2.11
[   44.226446] NET: Registered protocol family 31
[   44.226449] Bluetooth: HCI device and connection manager initialized
[   44.226454] Bluetooth: HCI socket layer initialized
[   44.240195] Bluetooth: L2CAP ver 2.9
[   44.240201] Bluetooth: L2CAP socket layer initialized
[   44.306255] Bluetooth: RFCOMM socket layer initialized
[   44.306270] Bluetooth: RFCOMM TTY layer initialized
[   44.306273] Bluetooth: RFCOMM ver 1.8
[   52.174658] hda-intel: Invalid position buffer, using LPIB read method instead.
[   63.385285] NET: Registered protocol family 10
[   63.386048] lo: Disabled Privacy Extensions
[   63.386619] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.387250] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.516606] NET: Registered protocol family 17
[   74.691853] wlan0: Initial auth_alg=0
[   74.691858] wlan0: authenticate with AP 00:1d:68:ef:7a:63
[   74.693743] wlan0: RX authentication from 00:1d:68:ef:7a:63 (alg=0 transaction=2 status=0)
[   74.693746] wlan0: authenticated
[   74.693748] wlan0: associate with AP 00:1d:68:ef:7a:63
[   74.696736] wlan0: RX AssocResp from 00:1d:68:ef:7a:63 (capab=0x411 status=0 aid=1)
[   74.696739] wlan0: associated
[   74.696743] wlan0: switched to short barker preamble (BSSID=00:1d:68:ef:7a:63)
[   74.699431] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   90.059160] wlan0: no IPv6 routers present

```
just had another crash here is a second dmesg output:

```
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519907
[    0.000000] Kernel command line: root=UUID=489ecafb-6d3c-4cf6-95e0-3d5f7026ac52 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.022 MHz processor.
[   22.511998] Console: colour VGA+ 80x25
[   22.512003] console [tty0] enabled
[   22.512280] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.512537] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.589581] Memory: 2065688k/2096000k available (2177k kernel code, 29088k reserved, 1006k data, 368k init, 1178496k highmem)
[   22.589588] virtual kernel memory layout:
[   22.589588]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.589589]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.589590]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.589591]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.589592]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.589592]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   22.589593]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   22.589596] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.589657] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.589789] hpet clockevent registered
[   22.669713] Calibrating delay using timer specific routine.. 4402.64 BogoMIPS (lpj=8805295)
[   22.669739] Security Framework initialized
[   22.669748] SELinux:  Disabled at boot.
[   22.669767] AppArmor: AppArmor initialized
[   22.669771] Failure registering capabilities with primary security module.
[   22.669779] Mount-cache hash table entries: 512
[   22.669922] Initializing cgroup subsys ns
[   22.669928] Initializing cgroup subsys cpuacct
[   22.669940] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   22.669946] monitor/mwait feature present.
[   22.669947] using mwait in idle threads.
[   22.669951] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.669953] CPU: L2 cache: 2048K
[   22.669956] CPU: Physical Processor ID: 0
[   22.669957] CPU: Processor Core ID: 0
[   22.669958] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   22.669967] Compat vDSO mapped to ffffe000.
[   22.669981] Checking 'hlt' instruction... OK.
[   22.686090] SMP alternatives: switching to UP code
[   22.687463] Early unpacking initramfs... done
[   22.961388] ACPI: Core revision 20070126
[   22.961433] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.964802] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   22.964816] SMP alternatives: switching to SMP code
[   22.965399] Booting processor 1/1 eip 3000
[   22.975592] Initializing CPU#1
[   23.053326] Calibrating delay using timer specific routine.. 4399.95 BogoMIPS (lpj=8799906)
[   23.053332] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   23.053336] monitor/mwait feature present.
[   23.053339] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.053340] CPU: L2 cache: 2048K
[   23.053342] CPU: Physical Processor ID: 0
[   23.053343] CPU: Processor Core ID: 1
[   23.053344] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   23.053816] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   23.053837] Total of 2 processors activated (8802.60 BogoMIPS).
[   23.054162] ENABLING IO-APIC IRQs
[   23.054344] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.201274] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.221268] Brought up 2 CPUs
[   23.221285] CPU0 attaching sched-domain:
[   23.221287]  domain 0: span 03
[   23.221288]   groups: 01 02
[   23.221291] CPU1 attaching sched-domain:
[   23.221292]  domain 0: span 03
[   23.221293]   groups: 02 01
[   23.221469] net_namespace: 64 bytes
[   23.221477] Booting paravirtualized kernel on bare hardware
[   23.221861] Time: 17:25:44  Date: 09/07/08
[   23.221883] NET: Registered protocol family 16
[   23.222023] EISA bus registered
[   23.222027] ACPI: bus type pci registered
[   23.229291] PCI: PCI BIOS revision 3.00 entry at 0xfa760, last bus=128
[   23.229293] PCI: Using configuration type 1
[   23.229305] Setting up standard PCI resources
[   23.230248] mtrr: your CPUs had inconsistent fixed MTRR settings
[   23.230249] mtrr: probably your BIOS does not setup all CPUs.
[   23.230251] mtrr: corrected configuration.
[   23.231831] ACPI: EC: Look up EC in DSDT
[   23.237795] ACPI: Interpreter enabled
[   23.237798] ACPI: (supports S0 S3 S4 S5)
[   23.237808] ACPI: Using IOAPIC for interrupt routing
[   23.243441] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.244974] PCI: Transparent bridge - 0000:00:13.1
[   23.245005] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.245188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[   23.245279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   23.245365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[   23.270324] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   23.270441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   23.270830] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[   23.270964] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   23.271098] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[   23.271232] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 6 7 10 11 12)
[   23.271357] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 *7 10 11 12)
[   23.271479] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0
[   23.271593] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.271715] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[   23.271833] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.271854] pnp: PnP ACPI init
[   23.271860] ACPI: bus type pnp registered
[   23.275076] pnp: PnP ACPI: found 15 devices
[   23.275078] ACPI: ACPI bus type pnp unregistered
[   23.275081] PnPBIOS: Disabled by ACPI PNP
[   23.275239] PCI: Using ACPI for IRQ routing
[   23.275241] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.224221] NET: Registered protocol family 8
[   24.224224] NET: Registered protocol family 20
[   24.224264] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[   24.224270] hpet0: 3 32-bit timers, 14318180 Hz
[   24.225299] AppArmor: AppArmor Filesystem Enabled
[   24.228219] Time: tsc clocksource has been installed.
[   24.228229] Switched to high resolution mode on CPU 0
[   24.228320] Switched to high resolution mode on CPU 1
[   24.244233] system 00:01: ioport range 0x400-0x47f has been reserved
[   24.244237] system 00:01: ioport range 0x500-0x50f has been reserved
[   24.244245] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   24.244248] system 00:02: ioport range 0x800-0x805 has been reserved
[   24.244252] system 00:02: ioport range 0x290-0x297 has been reserved
[   24.244255] system 00:02: ioport range 0x880-0x88f has been reserved
[   24.244268] system 00:09: iomem range 0xf0001000-0xf0001fff has been reserved
[   24.244276] system 00:0a: iomem range 0xf0002000-0xf0002fff has been reserved
[   24.244284] system 00:0b: iomem range 0xf0000000-0xf0000fff has been reserved
[   24.244292] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.244301] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
[   24.244305] system 00:0e: iomem range 0xfe800000-0xfe8000ff has been reserved
[   24.244309] system 00:0e: iomem range 0x7fee0000-0x7fefffff could not be reserved
[   24.244313] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   24.244317] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   24.244321] system 00:0e: iomem range 0x100000-0x7fedffff could not be reserved
[   24.244325] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.244329] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.244333] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
[   24.274632] PCI: Bridge: 0000:00:01.0
[   24.274635]   IO window: b000-bfff
[   24.274639]   MEM window: dfb00000-dfbfffff
[   24.274642]   PREFETCH window: dfe00000-dfefffff
[   24.274648] PCI: Bridge: 0000:00:02.0
[   24.274650]   IO window: a000-afff
[   24.274654]   MEM window: da000000-ddffffff
[   24.274657]   PREFETCH window: c0000000-cfffffff
[   24.274661] PCI: Bridge: 0000:00:03.0
[   24.274664]   IO window: c000-cfff
[   24.274668]   MEM window: dfd00000-dfdfffff
[   24.274672]   PREFETCH window: dfc00000-dfcfffff
[   24.274677] PCI: Bridge: 0000:00:13.1
[   24.274679]   IO window: 9000-9fff
[   24.274683]   MEM window: dfa00000-dfafffff
[   24.274686]   PREFETCH window: df900000-df9fffff
[   24.274701] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.274716] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
[   24.274721] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.274735] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
[   24.274740] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.274752] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   24.274760] NET: Registered protocol family 2
[   24.312190] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.312398] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.312917] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.313242] TCP: Hash tables configured (established 131072 bind 65536)
[   24.313244] TCP reno registered
[   24.324281] checking if image is initramfs... it is
[   24.862867] Freeing initrd memory: 7705k freed
[   24.863606] audit: initializing netlink socket (disabled)
[   24.863625] audit(1220808345.329:1): initialized
[   24.863825] highmem bounce pool size: 64 pages
[   24.865309] VFS: Disk quotas dquot_6.5.1
[   24.865366] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.865493] io scheduler noop registered
[   24.865494] io scheduler anticipatory registered
[   24.865496] io scheduler deadline registered
[   24.865504] io scheduler cfq registered (default)
[   24.865519] PCI: VIA PCI bridge detected. Disabling DAC.
[   24.865609] Boot video device is 0000:02:00.0
[   24.865710] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.865749] assign_interrupt_mode Found MSI capability
[   24.865797] Allocate Port Service[0000:00:02.0:pcie00]
[   24.865822] Allocate Port Service[0000:00:02.0:pcie02]
[   24.865895] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.865941] assign_interrupt_mode Found MSI capability
[   24.865991] Allocate Port Service[0000:00:03.0:pcie00]
[   24.866014] Allocate Port Service[0000:00:03.0:pcie02]
[   24.866215] isapnp: Scanning for PnP cards...
[   25.219991] isapnp: No Plug & Play device found
[   25.238764] Real Time Clock Driver v1.12ac
[   25.238945] hpet_resources: 0xfe800000 is busy
[   25.238998] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.239936] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.239990] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.240063] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   25.240064] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   25.240157] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.263263] mice: PS/2 mouse device common for all mice
[   25.263380] EISA: Probing bus 0 at eisa.0
[   25.263418] EISA: Detected 0 cards.
[   25.263421] cpuidle: using governor ladder
[   25.263422] cpuidle: using governor menu
[   25.263502] NET: Registered protocol family 1
[   25.263528] Using IPI No-Shortcut mode
[   25.263558] registered taskstats version 1
[   25.263658]   Magic number: 8:720:440
[   25.263752] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.263753] EDD information not available.
[   25.263931] Freeing unused kernel memory: 368k freed
[   25.286580] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.473971] fuse init (API version 7.9)
[   26.497078] ACPI: SSDT 7FEE9D00, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[   26.497239] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   26.497247] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   26.763390] SCSI subsystem initialized
[   26.768992] libata version 3.00 loaded.
[   26.770349] sata_via 0000:00:0f.0: version 2.3
[   26.770378] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18
[   26.770406] sata_via 0000:00:0f.0: routed to hard irq line 11
[   26.770448] scsi0 : sata_via
[   26.770486] scsi1 : sata_via
[   26.771495] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 18
[   26.771497] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 18
[   26.826007] usbcore: registered new interface driver usbfs
[   26.826028] usbcore: registered new interface driver hub
[   26.826049] usbcore: registered new device driver usb
[   26.827022] USB Universal Host Controller Interface driver v3.0
[   26.883727] 8139too Fast Ethernet driver 0.9.28
[   26.973399] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.137413] ata1.00: ATA-7: Hitachi HDT725025VLA380, V5DOA7BA, max UDMA/133
[   27.137417] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   27.153825] ata1.00: configured for UDMA/133
[   27.357026] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   27.367742] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5
[   27.367988] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 19
[   27.368001] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   27.368294] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   27.368317] uhci_hcd 0000:00:10.0: irq 19, io base 0x0000e000
[   27.368433] usb usb1: configuration #1 chosen from 1 choice
[   27.368452] hub 1-0:1.0: USB hub found
[   27.368455] hub 1-0:1.0: 2 ports detected
[   27.469026] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 20
[   27.469038] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   27.469071] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   27.469092] uhci_hcd 0000:00:10.1: irq 20, io base 0x0000dc00
[   27.469180] usb usb2: configuration #1 chosen from 1 choice
[   27.469198] hub 2-0:1.0: USB hub found
[   27.469202] hub 2-0:1.0: 2 ports detected
[   27.572902] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   27.572913] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   27.572941] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   27.572967] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d800
[   27.573046] usb usb3: configuration #1 chosen from 1 choice
[   27.573066] hub 3-0:1.0: USB hub found
[   27.573070] hub 3-0:1.0: 2 ports detected
[   27.676787] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21
[   27.676797] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   27.676823] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   27.676853] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[   27.676937] usb usb4: configuration #1 chosen from 1 choice
[   27.676953] hub 4-0:1.0: USB hub found
[   27.676957] hub 4-0:1.0: 2 ports detected
[   27.708660] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   27.781022] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[   27.781032] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   27.781051] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   27.781080] ehci_hcd 0000:00:10.4: irq 18, io mem 0xdffff000
[   27.852533] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.852692] usb usb5: configuration #1 chosen from 1 choice
[   27.852712] hub 5-0:1.0: USB hub found
[   27.852716] hub 5-0:1.0: 8 ports detected
[   27.958346] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 21 (level, low) -> IRQ 18
[   27.958863] eth0: RealTek RTL8139 at 0x9c00, 00:1c:25:30:24:dd, IRQ 18
[   27.958865] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   27.958896] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 20 (level, low) -> IRQ 19
[   28.011559] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfafe000-dfafe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   28.018215] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   28.020504] pata_via 0000:00:0f.1: version 0.3.3
[   28.020585] scsi2 : pata_via
[   28.020622] scsi3 : pata_via
[   28.021553] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[   28.021555] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[   28.026933] Driver 'sd' needs updating - please use bus_type methods
[   28.027003] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   28.027013] sd 0:0:0:0: [sda] Write Protect is off
[   28.027014] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.027027] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.027064] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   28.027072] sd 0:0:0:0: [sda] Write Protect is off
[   28.027073] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.027086] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.027088]  sda: sda1 sda2 sda3 sda4
[   28.072338] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.076711] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.248106] usb 1-1: device not accepting address 2, error -71
[   28.344362] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-H40N, RG01, max UDMA/66
[   28.516477] ata3.00: configured for UDMA/66
[   28.553580] Attempting manual resume
[   28.553583] swsusp: Resume From Partition 8:3
[   28.553584] PM: Checking swsusp image.
[   28.553716] PM: Resume from disk failed.
[   28.565078] EXT3-fs: INFO: recovery required on readonly filesystem.
[   28.565082] EXT3-fs: write access will be enabled during recovery.
[   28.675138] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H40N  RG01 PQ: 0 ANSI: 5
[   28.675243] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   28.681187] Driver 'sr' needs updating - please use bus_type methods
[   28.685123] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.685126] Uniform CD-ROM driver Revision: 3.20
[   28.685186] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   29.287189] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200043a579]
[   29.438915] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   29.709827] usb 5-1: configuration #1 chosen from 1 choice
[   29.946369] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   30.079379] usb 5-2: configuration #1 chosen from 1 choice
[   30.501788] usb 5-8: new high speed USB device using ehci_hcd and address 5
[   30.542476] kjournald starting.  Commit interval 5 seconds
[   30.542491] EXT3-fs: sda4: orphan cleanup on readonly fs
[   30.542500] ext3_orphan_cleanup: deleting unreferenced inode 843780
[   30.542541] ext3_orphan_cleanup: deleting unreferenced inode 623736
[   30.542570] ext3_orphan_cleanup: deleting unreferenced inode 1728523
[   30.542582] EXT3-fs: sda4: 3 orphan inodes deleted
[   30.542585] EXT3-fs: recovery complete.
[   30.581258] EXT3-fs: mounted filesystem with ordered data mode.
[   30.651345] usb 5-8: configuration #1 chosen from 1 choice
[   30.652919] usbcore: registered new interface driver libusual
[   30.656252] Initializing USB Mass Storage driver...
[   30.889401] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   31.070401] usb 2-1: configuration #1 chosen from 1 choice
[   31.073452] scsi4 : SCSI emulation for USB Mass Storage devices
[   31.073491] usb-storage: device found at 3
[   31.073493] usb-storage: waiting for device to settle before scanning
[   31.073518] scsi5 : SCSI emulation for USB Mass Storage devices
[   31.073549] usb-storage: device found at 5
[   31.073550] usb-storage: waiting for device to settle before scanning
[   31.073559] usbcore: registered new interface driver usb-storage
[   31.073561] USB Mass Storage support registered.
[   36.069282] usb-storage: device scan complete
[   36.069375] usb-storage: device scan complete
[   36.069772] scsi 4:0:0:0: Direct-Access     WD       3200AAJ External 1.06 PQ: 0 ANSI: 0
[   36.075780] scsi 5:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   36.082273] scsi 5:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   36.088891] scsi 5:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   36.095511] scsi 5:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   36.096762] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   36.096790] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   36.097910] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[   36.097945] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   36.099008] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[   36.099032] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   36.100128] sd 5:0:0:3: [sde] Attached SCSI removable disk
[   36.100155] sd 5:0:0:3: Attached scsi generic sg5 type 0
[   36.101477] sd 4:0:0:0: [sdf] 625142448 512-byte hardware sectors (320073 MB)
[   36.102145] sd 4:0:0:0: [sdf] Write Protect is off
[   36.102148] sd 4:0:0:0: [sdf] Mode Sense: 00 00 00 00
[   36.102149] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[   36.103097] sd 4:0:0:0: [sdf] 625142448 512-byte hardware sectors (320073 MB)
[   36.103722] sd 4:0:0:0: [sdf] Write Protect is off
[   36.103724] sd 4:0:0:0: [sdf] Mode Sense: 00 00 00 00
[   36.103726] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[   36.103728]  sdf:<6>input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.182541] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.243019] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.334863] Linux agpgart interface v0.102
[   37.408185] input: Power Button (FF) as /devices/virtual/input/input3
[   37.414845] agpgart: Detected VIA P4M890 chipset
[   37.421328] agpgart: AGP aperture is 128M @ 0xd0000000
[   37.458709] ACPI: Power Button (FF) [PWRF]
[   37.458766] input: Power Button (CM) as /devices/virtual/input/input4
[   37.514641] ACPI: Power Button (CM) [PWRB]
[   37.514696] input: Sleep Button (CM) as /devices/virtual/input/input5
[   37.562604] ACPI: Sleep Button (CM) [SLPB]
[   38.168395] nvidia: module license 'NVIDIA' taints kernel.
[   38.465874] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 22
[   38.465885] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   38.466019] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   38.516143] usbcore: registered new interface driver hiddev
[   38.557341] input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input6
[   38.603719] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:10.1-1
[   38.603735] usbcore: registered new interface driver usbhid
[   38.603739] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.666576] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 23
[   38.666606] PCI: Setting latency timer of device 0000:80:01.0 to 64
[   38.699269] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   38.951772] phy0: Selected rate control algorithm 'simple'
[   39.049510] usbcore: registered new interface driver rt73usb
[   39.066190] usbcore: registered new interface driver rt2500usb
[   41.907533]  sdf1
[   41.907607] sd 4:0:0:0: [sdf] Attached SCSI disk
[   41.907651] sd 4:0:0:0: Attached scsi generic sg6 type 0
[   42.181123] lp: driver loaded but no devices found
[   42.275475] Adding 9767512k swap on /dev/sda3.  Priority:-1 extents:1 across:9767512k
[   42.806812] EXT3 FS on sda4, internal journal
[   43.734880] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.076594] No dock devices found.
[   44.849740] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   44.849744] apm: disabled - APM is not SMP safe.
[   44.953140] ppdev: user-space parallel port driver
[   45.051574] audit(1220804765.959:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5195 profile="/usr/sbin/cupsd" namespace="default"
[   45.928017] eth0: link down
[   45.986895] Bluetooth: Core ver 2.11
[   45.986967] NET: Registered protocol family 31
[   45.986969] Bluetooth: HCI device and connection manager initialized
[   45.986972] Bluetooth: HCI socket layer initialized
[   46.018510] Bluetooth: L2CAP ver 2.9
[   46.018514] Bluetooth: L2CAP socket layer initialized
[   46.073288] Bluetooth: RFCOMM socket layer initialized
[   46.073302] Bluetooth: RFCOMM TTY layer initialized
[   46.073304] Bluetooth: RFCOMM ver 1.8
[   53.378772] hda-intel: Invalid position buffer, using LPIB read method instead.
[   70.543506] NET: Registered protocol family 10
[   70.543740] lo: Disabled Privacy Extensions
[   70.544066] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   70.544421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.950038] NET: Registered protocol family 17
[   80.122794] wlan0: Initial auth_alg=0
[   80.122805] wlan0: authenticate with AP 00:1d:68:ef:7a:63
[   80.124819] wlan0: RX authentication from 00:1d:68:ef:7a:63 (alg=0 transaction=2 status=0)
[   80.124828] wlan0: authenticated
[   80.124831] wlan0: associate with AP 00:1d:68:ef:7a:63
[   80.134181] wlan0: RX AssocResp from 00:1d:68:ef:7a:63 (capab=0x411 status=0 aid=3)
[   80.134192] wlan0: associated
[   80.134199] wlan0: switched to short barker preamble (BSSID=00:1d:68:ef:7a:63)
[   80.137564] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   94.137091] wlan0: no IPv6 routers present
peterbug@peterbug-desktop:~$ 


```

---

### Post by klotz on 2009-01-19
After an 8.04 LTS to 8.10 Intrepid upgrade, I'm having quite frequent crashes.  Either I come back and find a reboot has happened, or I see X programs start to behave very slowly (mouse etc) for a few seconds, then a reboot.

After reading this thread, I did the following, to no avail:
1. PowerNow (CPU Freq) was already off
2. Disabled ACPID and APMD (both were on, and it's not a laptop)
3. Switched from GPL 2D drivers to nVidia drivers, and switched back.
4. Installed the nvidia-180-modaliases package which had become available, and switched to nVidia drivers again.
5. Installed the linux-crashdump package described here:
[Kernel Crash Dumps]("http://www.linux-archive.org/ubuntu-development/113332-kernel-crash-dumps.html")  There it's called linux-crashdump-generic, but in the 8.10 release (unless I'm wrong) it's called just linux-crashdump.  This results in nothing; no files in /var/crash.

(I've had reboots in the distant past which were caused by bad power management on desktops; they weren't kernel panics, so I couldn't debug them as such.  I even got Alan Cox to help...it was that long ago.
But disabling APMD and ACPID has no effect this time.)

Does anybody know of linux-crashdump works or if it needs some enablement that was decided after the publication of the above referend linux-archive.org thread?  FWIW, there's nothing new in /boot/grub.ini after installing it; perhaps the changes are in some other grub or boot file?

---

### Post by hyperdude111 on 2009-01-19
It did on my:
Pentuim 4
512mb Ram
Nvidia geforce mx 440
80gb hdd

but not on my:
AMD Athlon 64x2
RAM Memory - 2048 MB
Hard Disk Capacity - 320 GB
Graphics Card - nVidia GeForce 1500 SE

---

### Post by w1go on 2009-01-23
i have the same problem. i turn the wireless connection roaming off, manualy set the wireless properties. so far so good.

---

### Post by w1go on 2009-01-23
it seems it wasn't the cure. my compaq cq40-108tu notepack still crashes but less often... are there any real solution?

---

### Post by UriahHeap on 2009-01-24
What I haven't seen suggested is try running  Ubuntu "Live" from the cd.  It will run with no updates, no configuration changes.  If it doesn't freeze then it is either software added to the full install, a proprietary driver or a configuration modification.  If it does freeze then it is either a hardware conflict or a glitch in Ubuntu for the system's hw configuration.

Uriah

---

### Post by jimv on 2009-01-24
All of you with the crashing problem, try this.  I had the same issue with Hardy, and installing a different kernel solved the issue.  The kernel is the "realtime" kernel, which I'm too lazy to look up exactly what the difference is, but it didn't seem to affect anything badly, and it made the crashing stop.

*If you are using the 64 bit version of Ubuntu, don't do this.

The command to run to install the alternative kernel is:

sudo apt-get install linux-rt

If you run into issues, your old kernel will still show up in the boot menu.

---

