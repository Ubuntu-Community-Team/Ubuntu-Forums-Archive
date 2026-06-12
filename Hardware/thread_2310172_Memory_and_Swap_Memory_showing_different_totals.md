---
title: "Memory and Swap Memory showing different totals"
date: 2016-01-16
forum: Hardware
---

### Post by Clueless Wonder on 2016-01-16
Hey everyone -

I have 4 gb memory installed, but am finding I am freezing up sometimes.  I looked at the Resources tab of System monitor and found that the Memory shows 800mb of 2.7gb and swap shows 6mb of 4.6gb.  Why doesn't the memory show 4.6gb?


Thanks!

Zak

---

### Post by Autodave on 2016-01-17
Bad memory chip(s)?  Sounds to me like something is running in the background that you don't know about. Go into task manager. Go to second drop down menu and click "Show all processes".  Now, scroll through there and look for one or more processes using a huga amount compared to the rest.

Report back.

---

### Post by buzzingrobot on 2016-01-17
"Memory" is the RAM the kernel finds on the machine.  "Swap" is a partition on a drive the kernel uses when not enough RAM is available.

Programs ask the kernel to allocate amounts of RAM for their use. If not enough unallocated RAM is available to meet a request, the kernel will make it available by writing a piece of allocated RAM to the swap partition, freeing that piece to be allocated.

---

### Post by mansonfan78 on 2016-01-17
I'd guess either bad ram (which can tested with memtest from grub), or your system has reserved a portion of ram for video memory (which you can check for in bios).

---

### Post by ajgreeny on 2016-01-17
What does the command ```
free -m
``` in terminal show you?

---

### Post by Clueless Wonder on 2016-01-17
Hey guys!  Thanks so much for the quick replies!

AutoDave - I am relatively new to Ubuntu.  By "task manager", do you mean System Monitor?  When I go in there and do the 3rd drop down of View All Processes, the largest one is Firefox at 290mb and Thunderbird at 105mb and Xorg at 90mb.  Everything else is 17mb and below.  Resources currently says 920mb is used, 0 swap.  

Mansonfan - I tried memtest.  It should 4 1gb instances of RAM.  After 5 hours, it said no errors.  Never ran it before, so don't know if I should have left it running.  It just kept going and appeared to be repeating itself...

Ajgreeny - when I run that command in terminal,  total is 2770, used is 2170, free is 600.  Swap total and free is 4709.

Please let me know any other thoughts or suggestions.  I really appreciate it!

---

### Post by ajgreeny on 2016-01-18
4GB ram installed but only 2770MB showing suggests you either have a fault somewhere in the memory modules or you have an integrated graphic card which uses a lot of your ram, ie approx 1.2GB memory used for graphics, which seems a lot to me.

More info on your hardware please.

---

### Post by Clueless Wonder on 2016-01-19
Hi AJgreeny -

thanks for your reply.  As I am still learning my way around ubuntu, what is the best way to get a list of the hardware you are looking for off of my computer?

---

### Post by ajgreeny on 2016-01-19
Can you please show us the full output of the free -m command that you have run already, using code-tags. See How-to in my signature below.

Highlight the output in the terminal and **right click ->Copy** then paste the output back here.

To check the memory seen in the machine by the BIOS you can either open the BIOS screen which will probably be by pressing a key at power-on shown by your computer in the few seconds after pressing the button.  You can also get a lot of info from terminal command ```
sudo lshw -c memory
``` and also paste that back here in code-tags.

Your graphic card can be seen from command ```
sudo lshw -c display
```

---

### Post by Clueless Wonder on 2016-01-19
Thanks for the great instructions!

free -m output

```
             total       used       free     shared    buffers     cached
Mem:          2770       2570        199          0        543       1017
-/+ buffers/cache:       1009       1760
Swap:         4709          0       4708


```

sudo lshw -c memory output

```
 *-firmware              
       description: BIOS
       vendor: Winbond Electronics
       physical id: 0
       version: A08
       date: 11/08/2005
       size: 64KiB
       capacity: 448KiB
       capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 16KiB
       capacity: 16KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 701
       size: 1MiB
       capacity: 1MiB
       capabilities: internal varies unified
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          vendor: 7F7F7F7F7F9B0000
          physical id: 0
          serial: FFFFFFFF
          slot: CHANNEL A DIMM 0
          size: 1GiB
          width: 64 bits
          clock: 533MHz (1.9ns)
     *-bank:1
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          vendor: 7F7F7F7F7F9B0000
          physical id: 1
          serial: FFFFFFFF
          slot: CHANNEL B DIMM 0
          size: 1GiB
          width: 64 bits
          clock: 533MHz (1.9ns)
     *-bank:2
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          vendor: 7F7F7F7F7F9B0000
          physical id: 2
          serial: FFFFFFFF
          slot: CHANNEL A DIMM 1
          size: 1GiB
          width: 64 bits
          clock: 533MHz (1.9ns)
     *-bank:3
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          vendor: 7F7F7F7F7F9B0000
          physical id: 3
          serial: FFFFFFFF
          slot: CHANNEL B DIMM 1
          size: 1GiB
          width: 64 bits
          clock: 533MHz (1.9ns)


```

sudo lshw -c display output

```
  *-display:0             
       description: Display controller
       product: RV370 [Radeon X300]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:b0000000-b7ffffff ioport:dc00(size=256) memory:dfde0000-dfdeffff memory:dfe00000-dfe1ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300 SE]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfdf0000-dfdfffff
  *-display
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS Rev. 2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:bc80(size=128) memory:df900000-df91ffff


```

---

### Post by ajgreeny on 2016-01-19
Well there are 4 memory modules detected in your machine, each of 1GB, so that confirms that you have 4GB total.

I see you also have both an AMD Radeon X300SE, which I think is integrated card but uses much less ram than 1.2GB, and also a stand-alone nvidia Geeforce 8400, though I can not find any info about the way that uses your ram; I thought the geeforce cards had their own dedicated memory, but I'm not sure and have never had an nvidia card.

---

### Post by Clueless Wonder on 2016-01-20
Thanks for reviewing my post ajgreeny.  I am thinking one thing I can try is removing the GForce card as I don't think I am using that right now.  

Is my computer using the full 4gb or only the 2.7?

Any other suggestions?

---

### Post by ajgreeny on 2016-01-20
Looks like only 2.7GB ram is being used, but that is where my knowledge of how ram is used by graphic cards may be giving you a wrong answer

---

### Post by mansonfan78 on 2016-01-20
Have you tried running a live dvd/usb of another distro and checking how much it sees?  That might help narrow down whether this a software or hardware issue.

---

### Post by Clueless Wonder on 2016-01-20
Thanks mansonfan78 - I will try that and report back.

---

### Post by Clueless Wonder on 2016-01-21
Hey guys -

I was doing some more reading.  Could it be that only 2.7gb is recognized because I am using 32bit software and on a 32 bit machine?  That doesn't really make sense to me, but not everything does....

I read on [this]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/") page to try  $ sudo apt-get install linux-generic-pae linux-headers-generic-pae.  Thought I would check here first if that makes sense with what I am dealing with.

---

### Post by Yellow Pasque on 2016-01-21
> Could it be that only 2.7gb is recognized because I am using 32bit software and on a 32 bit machine?

Yes.
[https://en.wikipedia.org/wiki/3_GB_barrier](https://en.wikipedia.org/wiki/3_GB_barrier)
[https://en.wikipedia.org/wiki/PCI_hole#Unavailable_memory](https://en.wikipedia.org/wiki/PCI_hole#Unavailable_memory)

The practical upshot of this is that you can't always work around these issues. I find that the BIOS or motherboard chipset is usually the limiting factor in how much RAM is actually usable.
1. Make sure you have latest BIOS and look in BIOS to see if it gives you an option for memory (hole) remapping or memory hoisting. Enable it if so.
2. Disable unused hardware if BIOS gives you the option. I disable serial port(s), firewire controller, onboard audio, etc. because I don't use them.
4. Use a 64-bit kernel/distro/OS if possible. Try a LiveUSB first if you're unsure whether this will help.

> I read on this page to try $ sudo apt-get install linux-generic-pae linux-headers-generic-pae
You probably already have these metapackages installed. The default 32-bit Ubuntu kernel has PAE enabled by default (in fact, Ubuntu won't run on older CPU's that don't support PAE). Again, the BIOS/mobo is often the thing that prevents PAE from working as intended.

> and on a 32 bit machine
Are you sure your CPU and chipset won't support 64-bit OS?
```
lspci
cat /proc/cpuinfo
```

---

### Post by Clueless Wonder on 2016-01-21
Mansonfan - I just did a live test with Puppy (32bit...did the test before I got Temujin's response) and it shows 2780mb total memory.

Thanks Temujin for the information.  I am confused as to why a 32 bit PC would come with 4gig capability if it can't see it....any thoughts?

I ran the code you suggested and got the following output:

```
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
04:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:02.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
04:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)
anon@dell:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 4
microcode    : 0x17
cpu MHz        : 3191.977
cache size    : 1024 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 6383.95
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

```

Based on what I read somewhere else, I think this is a 32bit only machine.

---

### Post by Yellow Pasque on 2016-01-21
Yeah, intel didn't start supporting memory remapping/hoisting until the 965 chipsets. You will probably see a bit more usable RAM if you pull one of the GPU's ) or disable it in case of onboard graphics. Are you using both of them?

> I am confused as to why a 32 bit PC would come with 4gig capability if it can't see it....any thoughts?
Marketing...

---

### Post by ajgreeny on 2016-01-21
Sorry; we should have thought about that possibility and asked if this was a 32 or 64 bit system; I just did not imagine that a 32 bit system would ship with 4GB ram, so that shows how marketing savvy I am!

You could easily try a 64 bit OS as a live system; if it boots you have a 64bit capable hardware setup, if it does not boot it will probably show an error message telling you it needs a 32bit kernel.

There is, unfortunately, not a lot that can be done to improve the situation if you do have 32bit hardware other than trying the forcepae boot option [https://help.ubuntu.com/community/BootOptions/before--after](https://help.ubuntu.com/community/BootOptions/before--after) but I have no experience of this so you will have to investigate further.

---

### Post by Clueless Wonder on 2016-01-22
Thanks ajgreeny and Temujin.

I will look into this further.  If it is the 32-bit CPU issue, any idea why the swap sees 4.6gb and the memory only sees the 2.7gb?  I would think if it was the CPU issue, swap wouldn't see it either.

---

### Post by mansonfan78 on 2016-01-22
Swap space is a separate partition of the hard drive and can be any size, memory refers to the actual ram.  I don't know about this being a 32 bit issue, my laptop has 4 gb of ram - I have both 64 bit Linux Mint and 32 bit Windows 10 installed and they both see the same amount of memory (4gb).

---

### Post by Yellow Pasque on 2016-01-22
> **mansonfan78 said:**
> I don't know about this being a 32 bit issue, my laptop has 4 gb of ram - I have both 64 bit Linux Mint and 32 bit Windows 10 installed and they both see the same amount of memory (4gb).

Yes, it's still very much a 32-bit issue. In your case, Windows 10 supports PAE (Windows 8 and up will not run on CPU's without it), and if your laptop is fairly recent, then your CPU and BIOS probably support PAE and memory remapping, which allows Windows 10 to address the full 4GB since the PCI hole will be moved above 4GB. The OP's mobo/BIOS does not support remapping the PCI hole above 4GB.

---

