---
title: "Creative Wbcam (VF0350) not working"
date: 2008-11-11
forum: Hardware
---

### Post by socngill on 2008-11-11
Recently bought a Creative Live! Cam Video IM but I can't get it to install.

I had already followed the steps here [http://ubuntuforums.org/showthread.php?t=966398&highlight=webcams+linux](http://ubuntuforums.org/showthread.php?t=966398&highlight=webcams+linux) when trying to install another cam (I got it to work but quality was really poor - the cam not linux) so bought this new one instead.  It didn't work, so I followed the instructions here [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource) I got the drivers through Adept but it still didn't work so I downloaded the tar.gz file and did the old cd directory, make, make install and it seemed all fine - no error messages, but the cam still doesn't work.

Have I tried installing too much stuff and it's all gone to pot, or is there something else I am doing wrong?  Have 10 days to send it back if I can't get it to work, but accoriding to this site [http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx) it should work.

Thanks.  Oh, running Kubuntu 8.10, I have apt-get updated it so it should all be upto date.

---

### Post by linux23dragon on 2008-11-11
*This is a double post I had written in response to your [[COLOR="Blue"]**[I]_message_***[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6154497&postcount=100")[/I]

Thanks for the report socngill.  

Is your webcam device reporting to be 041e:4060 ?.

I have had a look at the [[COLOR="Blue"]***_GSPA ov519 sub driver support list_***[/COLOR]]("http://moinejf.free.fr/webcam.html"), and found that the driver is not tested.  And Its not clear on what sensor is been used.  So I suspect that its possible that the driver is not production ready for that device.


You might be better off looking to get another webcam if you need one to work right now (since you can return the new cam).   

Have a look at the [[COLOR="Blue"]_***UVC based***_[/COLOR]]("http://linux-uvc.berlios.de/#devices") web cams as well.



EDIT:  I take it that you did read the [[COLOR="Blue"]***_FAQ_***[/COLOR]]("http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ") in regards to the ov51x-jpeg driver?

---

### Post by socngill on 2008-11-12
Thanks for the response.  That's really annoying because i specifically bought this webcam because the creative list here [http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx) says that this driver has been approved for this webcam.  

Can you recommend a good quality cam which definetely does work?  I can't keep sending the things back :lolflag:

---

### Post by socngill on 2008-11-12
> **linux23dragon said:**
> *This is a double post I had written in response to your [[COLOR="Blue"]**[I]_message_***[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6154497&postcount=100")[/I]

Thanks for the report socngill.  

Is your webcam device reporting to be 041e:4060 ?.

I have had a look at the [[COLOR="Blue"]***_GSPA ov519 sub driver support list_***[/COLOR]]("http://moinejf.free.fr/webcam.html"), and found that the driver is not tested.  And Its not clear on what sensor is been used.  So I suspect that its possible that the driver is not production ready for that device.


You might be better off looking to get another webcam if you need one to work right now (since you can return the new cam).   

Have a look at the [[COLOR="Blue"]_***UVC based***_[/COLOR]]("http://linux-uvc.berlios.de/#devices") web cams as well.



EDIT:  I take it that you did read the [[COLOR="Blue"]***_FAQ_***[/COLOR]]("http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ") in regards to the ov51x-jpeg driver?

Just found another list which would suggest it works as well:

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/Documentation/video4linux/gspca.txt#L35](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/Documentation/video4linux/gspca.txt#L35)

with ov519.  But that is the same driver I have tried to install?  isn't it?

I have had a look at the FAQ's and it is definetely plaugged into the USB directly (no hub being used).  however, how do I do this:

> The camera doesn't work with Skype

To work around it, you can try to load ov51x with the parameter forceblock=1 (version >= 1.5.6 required). Reference

Cheers.

---

### Post by linux23dragon on 2008-11-12
> **socngill said:**
> Just found another list which would suggest it works as well:

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/Documentation/video4linux/gspca.txt#L35](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/Documentation/video4linux/gspca.txt#L35)

with ov519.  But that is the same driver I have tried to install?  isn't it?


Correct, in fact, the one you have installed (by my instructions) is newer as well since it is directly downloaded from the developers.

> **socngill said:**
> 
I have had a look at the FAQ's and it is definetely plaugged into the USB directly (no hub being used).  however, how do I do this:

That looks to be a module loading option.  

Add this line into the ***/etc/modprobe.d/options*** file :-

```
options ov51x forceblock=1
```
Then reboot.

EDIT: you might need to use the command *modprobe -ae $(uname -r*)

Hope that helps.

---

### Post by linux23dragon on 2008-11-12
> **socngill said:**
> 
Can you recommend a good quality cam which definetely does work?  I can't keep sending the things back :lolflag:


Have a look at that supported UVC webcams list.  I have no idea what you need in regards to features, so by all means research the products you think will be good for you.

---

### Post by socngill on 2008-11-12
Thanks for your help.  I will give it a go this evening when i get home from work.  With any luck we can get this cam working.

---

### Post by socngill on 2008-11-12
> **linux23dragon said:**
> Have a look at that supported UVC webcams list.  I have no idea what you need in regards to features, so by all means research the products you think will be good for you.

I'll keep trying this one for a bit first.  Then if I can't get it working i shall check out the list.

OK, I have gone back to the begining,  I have unplugged the webcam, restarted the PC and added the suggested line to the file, it now reads:

> # Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1

options ov51x forceblock=1

If i have put it in the wrong place please let me know!!

Restared PC, plugged it in - nothing.  So I ran the following:

sudo apt-get install linux-backports-modules-2.6.27-7-generic

That installed successfully, so I restarted, and then when Kubuntu had fully loaded up I pluged the cam in.  Checked Cheese Webcam Booth but still says no camera.

So I ran the following:

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)

Restarted, but still nothing working.  lsusb shows the cam to be there:

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4067 Creative Technology, Ltd
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have not followed the enxt step ecause it says that it is for UVC only, and from the lists i have seen this cam does not use that driver.  

Any ideas what I could do next?  or do you think I should just give it up as a lost cause...?

Thanks.

---

### Post by linux23dragon on 2008-11-13
> **socngill said:**
> 

Any ideas what I could do next?  or do you think I should just give it up as a lost cause...?

Thanks.

Can you please copy the output of your kernel log when you plug in your web cam?

---

### Post by socngill on 2008-11-14
> **linux23dragon said:**
> Can you please copy the output of your kernel log when you plug in your web cam?

Here it is (it's quite long...)

> Nov 14 18:30:55 Kubuntu kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov 14 18:30:55 Kubuntu kernel: Cannot find map file.
Nov 14 18:30:55 Kubuntu kernel: Loaded 55959 symbols from 101 modules.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000004ff30000 (usable)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000004ff30000 - 000000004ff40000 (ACPI data)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000004ff40000 - 000000004fff0000 (ACPI NVS)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000004fff0000 - 0000000050000000 (reserved)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] last_pfn = 0x4ff30 max_arch_pfn = 0x100000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] RAMDISK: 377cd000 - 37fef9e1
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] DMI 2.3 present.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: RSDP 000F9E30, 0014 (r0 ACPIAM)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: RSDT 4FF30000, 0030 (r1 A M I  OEMRSDT   7000422 MSFT       97)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: FACP 4FF30200, 0081 (r2 A M I  OEMFACP   7000422 MSFT       97)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: DSDT 4FF303F0, 3797 (r1  P4CED P4CED105      105 INTL  2002026)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: FACS 4FF40000, 0040
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: APIC 4FF30390, 005C (r1 A M I  OEMAPIC   7000422 MSFT       97)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: OEMB 4FF40040, 003F (r1 A M I  OEMBIOS   7000422 MSFT       97)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] 383MB HIGHMEM available.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] 896MB LOWMEM available.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   mapped low ram: 0 - 38000000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   low ram: 00000000 - 38000000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   bootmap 00008000 - 0000f000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #4 [00377cd000 - 0037fef9e1]          RAMDISK ==> [00377cd000 - 0037fef9e1]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] found SMP MP-table at [c00ff780] 000ff780
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Zone PFN ranges:
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   HighMem  0x00038000 -> 0x0004ff30
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Movable zone start PFN for each node
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0004ff30
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] On node 0 totalpages: 327375
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Nov 14 18:30:55 Kubuntu kernel: [    0.000000]   HighMem zone: 97233 pages, LIFO batch:31
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:afb80000)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324496
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Kernel command line: root=UUID=ffa383af-0850-4dc3-adcf-4bd02067816c ro quiet splash
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Initializing CPU#0
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] TSC: using PMTIMER calibration value
Nov 14 18:30:55 Kubuntu kernel: [    0.000000] Detected 2665.343 MHz processor.
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] Console: colour VGA+ 80x25
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] console [tty0] enabled
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] Memory: 1282924k/1309888k available (2572k kernel code, 25664k reserved, 1160k data, 424k init, 392384k highmem)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] virtual kernel memory layout:
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Nov 14 18:30:55 Kubuntu kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 14 18:30:55 Kubuntu kernel: [    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 5330.68 BogoMIPS (lpj=10661372)
Nov 14 18:30:55 Kubuntu kernel: [    0.004047] Security Framework initialized
Nov 14 18:30:55 Kubuntu kernel: [    0.004059] SELinux:  Disabled at boot.
Nov 14 18:30:55 Kubuntu kernel: [    0.004090] AppArmor: AppArmor initialized
Nov 14 18:30:55 Kubuntu kernel: [    0.004106] Mount-cache hash table entries: 512
Nov 14 18:30:55 Kubuntu kernel: [    0.004354] Initializing cgroup subsys ns
Nov 14 18:30:55 Kubuntu kernel: [    0.004363] Initializing cgroup subsys cpuacct
Nov 14 18:30:55 Kubuntu kernel: [    0.004367] Initializing cgroup subsys memory
Nov 14 18:30:55 Kubuntu kernel: [    0.004393] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov 14 18:30:55 Kubuntu kernel: [    0.004397] CPU: L2 cache: 256K
Nov 14 18:30:55 Kubuntu kernel: [    0.004400] CPU: Hyper-Threading is disabled
Nov 14 18:30:55 Kubuntu kernel: [    0.004406] using mwait in idle threads.
Nov 14 18:30:55 Kubuntu kernel: [    0.004425] Checking 'hlt' instruction... OK.
Nov 14 18:30:55 Kubuntu kernel: [    0.020697] SMP alternatives: switching to UP code
Nov 14 18:30:55 Kubuntu kernel: [    0.031135] ACPI: Core revision 20080609
Nov 14 18:30:55 Kubuntu kernel: [    0.033461] ACPI: Checking initramfs for custom DSDT
Nov 14 18:30:55 Kubuntu kernel: [    0.409428] ENABLING IO-APIC IRQs
Nov 14 18:30:55 Kubuntu kernel: [    0.409612] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 14 18:30:55 Kubuntu kernel: [    0.449306] CPU0: Intel(R) Celeron(R) CPU 2.66GHz stepping 01
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] Brought up 1 CPUs
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] Total of 1 processors activated (5330.68 BogoMIPS).
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] CPU0 attaching sched-domain:
Nov 14 18:30:55 Kubuntu kernel: [    0.452028]  domain 0: span 0 level CPU
Nov 14 18:30:55 Kubuntu kernel: [    0.452028]   groups: 0
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] net_namespace: 840 bytes
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] Booting paravirtualized kernel on bare hardware
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] Time: 18:30:29  Date: 11/14/08
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] NET: Registered protocol family 16
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] EISA bus registered
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] ACPI: bus type pci registered
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
Nov 14 18:30:55 Kubuntu kernel: [    0.452028] PCI: Using configuration type 1 for base access
Nov 14 18:30:55 Kubuntu kernel: [    0.452682] ACPI: EC: Look up EC in DSDT
Nov 14 18:30:55 Kubuntu kernel: [    0.463716] ACPI: Interpreter enabled
Nov 14 18:30:55 Kubuntu kernel: [    0.463723] ACPI: (supports S0 S1 S3 S4 S5)
Nov 14 18:30:55 Kubuntu kernel: [    0.463751] ACPI: Using IOAPIC for interrupt routing
Nov 14 18:30:55 Kubuntu kernel: [    0.479548] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 14 18:30:55 Kubuntu kernel: [    0.479707] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, efffffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.479884] PCI: 0000:00:1d.0 reg 20 io port: [eec0, eedf]
Nov 14 18:30:55 Kubuntu kernel: [    0.479942] PCI: 0000:00:1d.1 reg 20 io port: [ef00, ef1f]
Nov 14 18:30:55 Kubuntu kernel: [    0.479999] PCI: 0000:00:1d.2 reg 20 io port: [ef20, ef3f]
Nov 14 18:30:55 Kubuntu kernel: [    0.480074] PCI: 0000:00:1d.3 reg 20 io port: [ef40, ef5f]
Nov 14 18:30:55 Kubuntu kernel: [    0.480140] PCI: 0000:00:1d.7 reg 10 32bit mmio: [febff800, febffbff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480198] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Nov 14 18:30:55 Kubuntu kernel: [    0.480204] pci 0000:00:1d.7: PME# disabled
Nov 14 18:30:55 Kubuntu kernel: [    0.480297] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Nov 14 18:30:55 Kubuntu kernel: [    0.480306] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Nov 14 18:30:55 Kubuntu kernel: [    0.480311] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Nov 14 18:30:55 Kubuntu kernel: [    0.480333] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
Nov 14 18:30:55 Kubuntu kernel: [    0.480341] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
Nov 14 18:30:55 Kubuntu kernel: [    0.480348] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
Nov 14 18:30:55 Kubuntu kernel: [    0.480356] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
Nov 14 18:30:55 Kubuntu kernel: [    0.480364] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]
Nov 14 18:30:55 Kubuntu kernel: [    0.480372] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480426] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
Nov 14 18:30:55 Kubuntu kernel: [    0.480504] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480512] PCI: 0000:01:00.0 reg 14 io port: [b000, b0ff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480519] PCI: 0000:01:00.0 reg 18 32bit mmio: [fe8f0000, fe8fffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480542] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe8c0000, fe8dffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480565] pci 0000:01:00.0: supports D1
Nov 14 18:30:55 Kubuntu kernel: [    0.480567] pci 0000:01:00.0: supports D2
Nov 14 18:30:55 Kubuntu kernel: [    0.480599] PCI: 0000:01:00.1 reg 10 32bit mmio: [fe8e0000, fe8effff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480645] pci 0000:01:00.1: supports D1
Nov 14 18:30:55 Kubuntu kernel: [    0.480647] pci 0000:01:00.1: supports D2
Nov 14 18:30:55 Kubuntu kernel: [    0.480692] PCI: bridge 0000:00:01.0 io port: [b000, bfff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480696] PCI: bridge 0000:00:01.0 32bit mmio: [fe800000, fe8fffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480702] PCI: bridge 0000:00:01.0 32bit mmio pref: [bff00000, dfefffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480738] PCI: 0000:02:01.0 reg 10 32bit mmio: [fe9e0000, fe9fffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480750] PCI: 0000:02:01.0 reg 18 io port: [cf80, cf9f]
Nov 14 18:30:55 Kubuntu kernel: [    0.480782] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
Nov 14 18:30:55 Kubuntu kernel: [    0.480788] pci 0000:02:01.0: PME# disabled
Nov 14 18:30:55 Kubuntu kernel: [    0.480825] PCI: bridge 0000:00:03.0 io port: [c000, cfff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480830] PCI: bridge 0000:00:03.0 32bit mmio: [fe900000, fe9fffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480874] PCI: 0000:03:03.0 reg 10 32bit mmio: [feaff800, feafffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.480883] PCI: 0000:03:03.0 reg 14 io port: [dc00, dc7f]
Nov 14 18:30:55 Kubuntu kernel: [    0.480924] pci 0000:03:03.0: supports D2
Nov 14 18:30:55 Kubuntu kernel: [    0.480927] pci 0000:03:03.0: PME# supported from D2 D3hot D3cold
Nov 14 18:30:55 Kubuntu kernel: [    0.480932] pci 0000:03:03.0: PME# disabled
Nov 14 18:30:55 Kubuntu kernel: [    0.480973] PCI: 0000:03:0c.0 reg 10 io port: [d800, d8ff]
Nov 14 18:30:55 Kubuntu kernel: [    0.481019] pci 0000:03:0c.0: supports D1
Nov 14 18:30:55 Kubuntu kernel: [    0.481021] pci 0000:03:0c.0: supports D2
Nov 14 18:30:55 Kubuntu kernel: [    0.481048] pci 0000:00:1e.0: transparent bridge
Nov 14 18:30:55 Kubuntu kernel: [    0.481053] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
Nov 14 18:30:55 Kubuntu kernel: [    0.481058] PCI: bridge 0000:00:1e.0 32bit mmio: [fea00000, feafffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.481080] bus 00 -> node 0
Nov 14 18:30:55 Kubuntu kernel: [    0.481095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 14 18:30:55 Kubuntu kernel: [    0.481338] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov 14 18:30:55 Kubuntu kernel: [    0.481788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
Nov 14 18:30:55 Kubuntu kernel: [    0.493273] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 14 18:30:55 Kubuntu kernel: [    0.493462] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 14 18:30:55 Kubuntu kernel: [    0.493646] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 14 18:30:55 Kubuntu kernel: [    0.493832] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 14 18:30:55 Kubuntu kernel: [    0.494018] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 14 18:30:55 Kubuntu kernel: [    0.494203] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 14 18:30:55 Kubuntu kernel: [    0.494390] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 14 18:30:55 Kubuntu kernel: [    0.494577] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov 14 18:30:55 Kubuntu kernel: [    0.494946] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - EE, should be DF [20080609]
Nov 14 18:30:55 Kubuntu kernel: [    0.494960] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 14 18:30:55 Kubuntu kernel: [    0.495054] pnp: PnP ACPI init
Nov 14 18:30:55 Kubuntu kernel: [    0.495071] ACPI: bus type pnp registered
Nov 14 18:30:55 Kubuntu kernel: [    0.504399] pnp: PnP ACPI: found 15 devices
Nov 14 18:30:55 Kubuntu kernel: [    0.504405] ACPI: ACPI bus type pnp unregistered
Nov 14 18:30:55 Kubuntu kernel: [    0.504412] PnPBIOS: Disabled by ACPI PNP
Nov 14 18:30:55 Kubuntu kernel: [    0.505238] PCI: Using ACPI for IRQ routing
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] NET: Registered protocol family 8
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] NET: Registered protocol family 20
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] NetLabel: Initializing
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] NetLabel:  domain hash size = 128
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] NetLabel:  unlabeled traffic allowed by default
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] hpet clockevent registered
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 14 18:30:55 Kubuntu kernel: [    0.505451] hpet0: 3 64-bit timers, 14318180 Hz
Nov 14 18:30:55 Kubuntu kernel: [    0.505963] tracer: 772 pages allocated for 65536 entries of 48 bytes
Nov 14 18:30:55 Kubuntu kernel: [    0.505967]    actual entries 65620
Nov 14 18:30:55 Kubuntu kernel: [    0.506182] AppArmor: AppArmor Filesystem Enabled
Nov 14 18:30:55 Kubuntu kernel: [    0.506211] ACPI: RTC can wake from S4
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0b: ioport range 0x680-0x6ff has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0b: ioport range 0x290-0x297 has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0c: ioport range 0x800-0x87f has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0c: ioport range 0x480-0x4bf has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0c: iomem range 0xffb00000-0xffbfffff could not be reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0e: iomem range 0x100000-0x4ffeffff could not be reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.506252] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
Nov 14 18:30:55 Kubuntu kernel: [    0.543580] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov 14 18:30:55 Kubuntu kernel: [    0.543587] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
Nov 14 18:30:55 Kubuntu kernel: [    0.543594] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe8fffff
Nov 14 18:30:55 Kubuntu kernel: [    0.543599] pci 0000:00:01.0:   PREFETCH window: 0x000000bff00000-0x000000dfefffff
Nov 14 18:30:55 Kubuntu kernel: [    0.543607] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
Nov 14 18:30:55 Kubuntu kernel: [    0.543611] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
Nov 14 18:30:55 Kubuntu kernel: [    0.543618] pci 0000:00:03.0:   MEM window: 0xfe900000-0xfe9fffff
Nov 14 18:30:55 Kubuntu kernel: [    0.543622] pci 0000:00:03.0:   PREFETCH window: disabled
Nov 14 18:30:55 Kubuntu kernel: [    0.543630] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Nov 14 18:30:55 Kubuntu kernel: [    0.543634] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
Nov 14 18:30:55 Kubuntu kernel: [    0.543641] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
Nov 14 18:30:55 Kubuntu kernel: [    0.543646] pci 0000:00:1e.0:   PREFETCH window: disabled
Nov 14 18:30:55 Kubuntu kernel: [    0.543674] pci 0000:00:1e.0: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    0.543679] bus: 00 index 0 io port: [0, ffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543682] bus: 00 index 1 mmio: [0, ffffffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543685] bus: 01 index 0 io port: [b000, bfff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543688] bus: 01 index 1 mmio: [fe800000, fe8fffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543690] bus: 01 index 2 mmio: [bff00000, dfefffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543693] bus: 01 index 3 mmio: [0, 0]
Nov 14 18:30:55 Kubuntu kernel: [    0.543695] bus: 02 index 0 io port: [c000, cfff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543698] bus: 02 index 1 mmio: [fe900000, fe9fffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543700] bus: 02 index 2 mmio: [0, 0]
Nov 14 18:30:55 Kubuntu kernel: [    0.543703] bus: 02 index 3 mmio: [0, 0]
Nov 14 18:30:55 Kubuntu kernel: [    0.543705] bus: 03 index 0 io port: [d000, dfff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543708] bus: 03 index 1 mmio: [fea00000, feafffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543710] bus: 03 index 2 mmio: [0, 0]
Nov 14 18:30:55 Kubuntu kernel: [    0.543713] bus: 03 index 3 io port: [0, ffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543715] bus: 03 index 4 mmio: [0, ffffffff]
Nov 14 18:30:55 Kubuntu kernel: [    0.543733] NET: Registered protocol family 2
Nov 14 18:30:55 Kubuntu kernel: [    0.543989] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    0.544453] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    0.545533] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    0.546139] TCP: Hash tables configured (established 131072 bind 65536)
Nov 14 18:30:55 Kubuntu kernel: [    0.546145] TCP reno registered
Nov 14 18:30:55 Kubuntu kernel: [    0.546381] NET: Registered protocol family 1
Nov 14 18:30:55 Kubuntu kernel: [    0.546576] checking if image is initramfs... it is
Nov 14 18:30:55 Kubuntu kernel: [    1.008084] Switched to high resolution mode on CPU 0
Nov 14 18:30:55 Kubuntu kernel: [    1.338147] Freeing initrd memory: 8330k freed
Nov 14 18:30:55 Kubuntu kernel: [    1.339603] audit: initializing netlink socket (disabled)
Nov 14 18:30:55 Kubuntu kernel: [    1.339625] type=2000 audit(1226687429.336:1): initialized
Nov 14 18:30:55 Kubuntu kernel: [    1.345676] highmem bounce pool size: 64 pages
Nov 14 18:30:55 Kubuntu kernel: [    1.345689] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov 14 18:30:55 Kubuntu kernel: [    1.349759] VFS: Disk quotas dquot_6.5.1
Nov 14 18:30:55 Kubuntu kernel: [    1.349949] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 14 18:30:55 Kubuntu kernel: [    1.350160] msgmni has been set to 1757
Nov 14 18:30:55 Kubuntu kernel: [    1.350405] io scheduler noop registered
Nov 14 18:30:55 Kubuntu kernel: [    1.350410] io scheduler anticipatory registered
Nov 14 18:30:55 Kubuntu kernel: [    1.350413] io scheduler deadline registered
Nov 14 18:30:55 Kubuntu kernel: [    1.350439] io scheduler cfq registered (default)
Nov 14 18:30:55 Kubuntu kernel: [    1.350546] pci 0000:01:00.0: Boot video device
Nov 14 18:30:55 Kubuntu kernel: [    1.351272] isapnp: Scanning for PnP cards...
Nov 14 18:30:55 Kubuntu kernel: [    1.703059] isapnp: No Plug & Play device found
Nov 14 18:30:55 Kubuntu kernel: [    1.822684] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Nov 14 18:30:55 Kubuntu kernel: [    1.822881] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 14 18:30:55 Kubuntu kernel: [    1.823283] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 14 18:30:55 Kubuntu kernel: [    1.825072] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 14 18:30:55 Kubuntu kernel: [    1.825947] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 14 18:30:55 Kubuntu kernel: [    1.829802] brd: module loaded
Nov 14 18:30:55 Kubuntu kernel: [    1.829941] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 14 18:30:55 Kubuntu kernel: [    1.830200] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 14 18:30:55 Kubuntu kernel: [    1.833108] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 14 18:30:55 Kubuntu kernel: [    1.833122] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 14 18:30:55 Kubuntu kernel: [    1.834144] mice: PS/2 mouse device common for all mice
Nov 14 18:30:55 Kubuntu kernel: [    1.834561] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Nov 14 18:30:55 Kubuntu kernel: [    1.834592] rtc0: alarms up to one month, hpet irqs
Nov 14 18:30:55 Kubuntu kernel: [    1.834874] EISA: Probing bus 0 at eisa.0
Nov 14 18:30:55 Kubuntu kernel: [    1.834916] EISA: Detected 0 cards.
Nov 14 18:30:55 Kubuntu kernel: [    1.834921] cpuidle: using governor ladder
Nov 14 18:30:55 Kubuntu kernel: [    1.834924] cpuidle: using governor menu
Nov 14 18:30:55 Kubuntu kernel: [    1.835678] TCP cubic registered
Nov 14 18:30:55 Kubuntu kernel: [    1.835729] Using IPI No-Shortcut mode
Nov 14 18:30:55 Kubuntu kernel: [    1.836528] registered taskstats version 1
Nov 14 18:30:55 Kubuntu kernel: [    1.836659]   Magic number: 0:470:544
Nov 14 18:30:55 Kubuntu kernel: [    1.836830] rtc_cmos 00:02: setting system clock to 2008-11-14 18:30:31 UTC (1226687431)
Nov 14 18:30:55 Kubuntu kernel: [    1.836836] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 14 18:30:55 Kubuntu kernel: [    1.836839] EDD information not available.
Nov 14 18:30:55 Kubuntu kernel: [    1.837323] Freeing unused kernel memory: 424k freed
Nov 14 18:30:55 Kubuntu kernel: [    1.837393] Write protecting the kernel text: 2576k
Nov 14 18:30:55 Kubuntu kernel: [    1.837434] Write protecting the kernel read-only data: 936k
Nov 14 18:30:55 Kubuntu kernel: [    1.863230] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 14 18:30:55 Kubuntu kernel: [    2.086094] fuse init (API version 7.9)
Nov 14 18:30:55 Kubuntu kernel: [    2.354242] processor ACPI0007:00: registered as cooling_device0
Nov 14 18:30:55 Kubuntu kernel: [    3.280987] usbcore: registered new interface driver usbfs
Nov 14 18:30:55 Kubuntu kernel: [    3.281028] usbcore: registered new interface driver hub
Nov 14 18:30:55 Kubuntu kernel: [    3.288281] Intel(R) PRO/1000 Network Driver - version 7.3.20-k3-NAPI
Nov 14 18:30:55 Kubuntu kernel: [    3.288287] Copyright (c) 1999-2006 Intel Corporation.
Nov 14 18:30:55 Kubuntu kernel: [    3.288346] e1000 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 14 18:30:55 Kubuntu kernel: [    3.288357] e1000 0000:02:01.0: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    3.299461] usbcore: registered new device driver usb
Nov 14 18:30:55 Kubuntu kernel: [    3.302703] USB Universal Host Controller Interface driver v3.0
Nov 14 18:30:55 Kubuntu kernel: [    3.436620] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0c:6e:b6:ea:56
Nov 14 18:30:55 Kubuntu kernel: [    3.445009] No dock devices found.
Nov 14 18:30:55 Kubuntu kernel: [    3.533029] SCSI subsystem initialized
Nov 14 18:30:55 Kubuntu kernel: [    3.573556] libata version 3.00 loaded.
Nov 14 18:30:55 Kubuntu kernel: [    3.722662] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Nov 14 18:30:55 Kubuntu kernel: [    3.722759] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 14 18:30:55 Kubuntu kernel: [    3.722773] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    3.722779] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 14 18:30:55 Kubuntu kernel: [    3.722853] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov 14 18:30:55 Kubuntu kernel: [    3.722891] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
Nov 14 18:30:55 Kubuntu kernel: [    3.723165] usb usb1: configuration #1 chosen from 1 choice
Nov 14 18:30:55 Kubuntu kernel: [    3.723213] hub 1-0:1.0: USB hub found
Nov 14 18:30:55 Kubuntu kernel: [    3.723237] hub 1-0:1.0: 2 ports detected
Nov 14 18:30:55 Kubuntu kernel: [    3.824597] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 14 18:30:55 Kubuntu kernel: [    3.824613] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    3.824618] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 14 18:30:55 Kubuntu kernel: [    3.824676] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov 14 18:30:55 Kubuntu kernel: [    3.824715] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ef00
Nov 14 18:30:55 Kubuntu kernel: [    3.824967] usb usb2: configuration #1 chosen from 1 choice
Nov 14 18:30:55 Kubuntu kernel: [    3.825014] hub 2-0:1.0: USB hub found
Nov 14 18:30:55 Kubuntu kernel: [    3.825031] hub 2-0:1.0: 2 ports detected
Nov 14 18:30:55 Kubuntu kernel: [    4.032603] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 14 18:30:55 Kubuntu kernel: [    4.032618] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    4.032623] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 14 18:30:55 Kubuntu kernel: [    4.032683] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Nov 14 18:30:55 Kubuntu kernel: [    4.032723] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
Nov 14 18:30:55 Kubuntu kernel: [    4.032991] usb usb3: configuration #1 chosen from 1 choice
Nov 14 18:30:55 Kubuntu kernel: [    4.033040] hub 3-0:1.0: USB hub found
Nov 14 18:30:55 Kubuntu kernel: [    4.033056] hub 3-0:1.0: 2 ports detected
Nov 14 18:30:55 Kubuntu kernel: [    4.136594] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 14 18:30:55 Kubuntu kernel: [    4.136609] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    4.136614] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov 14 18:30:55 Kubuntu kernel: [    4.136663] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Nov 14 18:30:55 Kubuntu kernel: [    4.136695] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
Nov 14 18:30:55 Kubuntu kernel: [    4.136954] usb usb4: configuration #1 chosen from 1 choice
Nov 14 18:30:55 Kubuntu kernel: [    4.137008] hub 4-0:1.0: USB hub found
Nov 14 18:30:55 Kubuntu kernel: [    4.137022] hub 4-0:1.0: 2 ports detected
Nov 14 18:30:55 Kubuntu kernel: [    4.144102] usb 2-1: new full speed USB device using uhci_hcd and address 2
Nov 14 18:30:55 Kubuntu kernel: [    4.240632] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Nov 14 18:30:55 Kubuntu kernel: [    4.240654] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    4.240659] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 14 18:30:55 Kubuntu kernel: [    4.240712] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Nov 14 18:30:55 Kubuntu kernel: [    4.244631] ehci_hcd 0000:00:1d.7: debug port 1
Nov 14 18:30:55 Kubuntu kernel: [    4.244640] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
Nov 14 18:30:55 Kubuntu kernel: [    4.244659] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff800
Nov 14 18:30:55 Kubuntu kernel: [    4.268084] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 14 18:30:55 Kubuntu kernel: [    4.268386] usb usb5: configuration #1 chosen from 1 choice
Nov 14 18:30:55 Kubuntu kernel: [    4.268436] hub 5-0:1.0: USB hub found
Nov 14 18:30:55 Kubuntu kernel: [    4.268452] hub 5-0:1.0: 8 ports detected
Nov 14 18:30:55 Kubuntu kernel: [    4.479096] ata_piix 0000:00:1f.1: version 2.12
Nov 14 18:30:55 Kubuntu kernel: [    4.479114] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Nov 14 18:30:55 Kubuntu kernel: [    4.479124] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 14 18:30:55 Kubuntu kernel: [    4.479187] ata_piix 0000:00:1f.1: setting latency timer to 64
Nov 14 18:30:55 Kubuntu kernel: [    4.480914] scsi0 : ata_piix
Nov 14 18:30:55 Kubuntu kernel: [    4.481115] scsi1 : ata_piix
Nov 14 18:30:55 Kubuntu kernel: [    4.483700] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Nov 14 18:30:55 Kubuntu kernel: [    4.483705] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Nov 14 18:30:55 Kubuntu kernel: [    4.664099] usb 2-1: device not accepting address 2, error -71
Nov 14 18:30:55 Kubuntu kernel: [    4.676364] ata1.01: HPA unlocked: 240119615 -> 240121728, native 240121728
Nov 14 18:30:55 Kubuntu kernel: [    4.676374] ata1.01: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
Nov 14 18:30:55 Kubuntu kernel: [    4.676378] ata1.01: 240121728 sectors, multi 16: LBA 
Nov 14 18:30:55 Kubuntu kernel: [    4.692500] ata1.01: configured for UDMA/100
Nov 14 18:30:55 Kubuntu kernel: [    4.720059] hub 2-0:1.0: unable to enumerate USB device on port 1
Nov 14 18:30:55 Kubuntu kernel: [    4.848198] ata2.01: NODEV after polling detection
Nov 14 18:30:55 Kubuntu kernel: [    4.856584] ata2.00: ATAPI: NU      DVDRW DDW-081, BX32, max UDMA/33
Nov 14 18:30:55 Kubuntu kernel: [    4.872604] ata2.00: configured for UDMA/33
Nov 14 18:30:55 Kubuntu kernel: [    4.872794] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
Nov 14 18:30:55 Kubuntu kernel: [    4.875268] scsi 1:0:0:0: CD-ROM            NU       DVDRW DDW-081    BX32 PQ: 0 ANSI: 5
Nov 14 18:30:55 Kubuntu kernel: [    4.876681] ohci1394 0000:03:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 14 18:30:55 Kubuntu kernel: [    4.929476] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 14 18:30:55 Kubuntu kernel: [    4.983400] scsi 0:0:1:0: Attached scsi generic sg0 type 0
Nov 14 18:30:55 Kubuntu kernel: [    4.983522] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Nov 14 18:30:55 Kubuntu kernel: [    5.016882] Driver 'sd' needs updating - please use bus_type methods
Nov 14 18:30:55 Kubuntu kernel: [    5.019741] sd 0:0:1:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Nov 14 18:30:55 Kubuntu kernel: [    5.019778] sd 0:0:1:0: [sda] Write Protect is off
Nov 14 18:30:55 Kubuntu kernel: [    5.019783] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Nov 14 18:30:55 Kubuntu kernel: [    5.019837] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 14 18:30:55 Kubuntu kernel: [    5.019983] sd 0:0:1:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Nov 14 18:30:55 Kubuntu kernel: [    5.020073] sd 0:0:1:0: [sda] Write Protect is off
Nov 14 18:30:55 Kubuntu kernel: [    5.020078] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Nov 14 18:30:55 Kubuntu kernel: [    5.020142] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 14 18:30:55 Kubuntu kernel: [    5.020149]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Nov 14 18:30:55 Kubuntu kernel: [    5.041770]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10<6>usb 2-1: new full speed USB device using uhci_hcd and address 4
Nov 14 18:30:55 Kubuntu kernel: [    5.150311]  sda11 >
Nov 14 18:30:55 Kubuntu kernel: [    5.150776] sd 0:0:1:0: [sda] Attached SCSI disk
Nov 14 18:30:55 Kubuntu kernel: [    5.164851] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Nov 14 18:30:55 Kubuntu kernel: [    5.164860] Uniform CD-ROM driver Revision: 3.20
Nov 14 18:30:55 Kubuntu kernel: [    5.165012] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov 14 18:30:55 Kubuntu kernel: [    5.333817] usb 2-1: configuration #1 chosen from 1 choice
Nov 14 18:30:55 Kubuntu kernel: [    5.774448] PM: Starting manual resume from disk
Nov 14 18:30:55 Kubuntu kernel: [    5.774456] PM: Resume from partition 8:10
Nov 14 18:30:55 Kubuntu kernel: [    5.774458] PM: Checking hibernation image.
Nov 14 18:30:55 Kubuntu kernel: [    5.774716] PM: Resume from disk failed.
Nov 14 18:30:55 Kubuntu kernel: [    5.828344] kjournald starting.  Commit interval 5 seconds
Nov 14 18:30:55 Kubuntu kernel: [    5.828372] EXT3-fs: mounted filesystem with ordered data mode.
Nov 14 18:30:55 Kubuntu kernel: [    6.208194] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000033b54c]
Nov 14 18:30:55 Kubuntu kernel: [   13.067517] udevd version 124 started
Nov 14 18:30:55 Kubuntu kernel: [   13.852526] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 14 18:30:55 Kubuntu kernel: [   13.911893] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 14 18:30:55 Kubuntu kernel: [   13.977526] EDAC MC: Ver: 2.1.0 Nov  4 2008
Nov 14 18:30:55 Kubuntu kernel: [   14.050653] EDAC i82875p: i82875p init one
Nov 14 18:30:55 Kubuntu kernel: [   14.050698] PCI: 0000:00:06.0 reg 10 32bit mmio: [fecf0000, fecf0fff]
Nov 14 18:30:55 Kubuntu kernel: [   14.051704] pci 0000:00:06.0: device not available because of BAR 0 [0xfecf0000-0xfecf0fff] collisions
Nov 14 18:30:55 Kubuntu kernel: [   14.051712] EDAC i82875p: i82875p_setup_overfl_dev(): Failed to enable overflow device
Nov 14 18:30:55 Kubuntu kernel: [   14.198136] Linux agpgart interface v0.103
Nov 14 18:30:55 Kubuntu kernel: [   14.270794] agpgart-intel 0000:00:00.0: Intel i875 Chipset
Nov 14 18:30:55 Kubuntu kernel: [   14.354422] iTCO_vendor_support: vendor-support=0
Nov 14 18:30:55 Kubuntu kernel: [   14.411925] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Nov 14 18:30:55 Kubuntu kernel: [   14.413894] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
Nov 14 18:30:55 Kubuntu kernel: [   14.414781] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Nov 14 18:30:55 Kubuntu kernel: [   14.415109] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov 14 18:30:55 Kubuntu kernel: [   14.555148] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov 14 18:30:55 Kubuntu kernel: [   14.568058] ACPI: Power Button (FF) [PWRF]
Nov 14 18:30:55 Kubuntu kernel: [   14.568271] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov 14 18:30:55 Kubuntu kernel: [   14.580042] ACPI: Power Button (CM) [PWRB]
Nov 14 18:30:55 Kubuntu kernel: [   14.614255] intel_rng: FWH not detected
Nov 14 18:30:55 Kubuntu kernel: [   15.350222] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 14 18:30:55 Kubuntu kernel: [   15.350330] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov 14 18:30:55 Kubuntu kernel: [   15.635789] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 14 18:30:55 Kubuntu kernel: [   15.986146] [fglrx] Maximum main memory to use for locked dma buffers: 1169 MBytes.
Nov 14 18:30:55 Kubuntu kernel: [   15.986372] [fglrx]   vendor: 1002 device: 71c1 count: 1
Nov 14 18:30:55 Kubuntu kernel: [   15.986844] [fglrx] ioport: bar 1, base 0xb000, size: 0x100
Nov 14 18:30:55 Kubuntu kernel: [   15.986866] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 14 18:30:55 Kubuntu kernel: [   15.987376] [fglrx] PAT is enabled successfully!
Nov 14 18:30:55 Kubuntu kernel: [   15.987419] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
Nov 14 18:30:55 Kubuntu kernel: [   16.354319] Linux video capture interface: v2.00
Nov 14 18:30:55 Kubuntu kernel: [   16.428607] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [   16.428613] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [   16.429266] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [   16.429270] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [   16.429505] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [   16.429508] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [   16.429626] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [   16.429629] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [   16.430046] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [   16.430048] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [   16.430148] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [   16.430151] ov51x_jpeg: Unknown symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [   16.433657] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [   16.433666] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [   16.434310] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [   16.434314] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [   16.434547] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [   16.434551] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [   16.434668] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [   16.434671] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [   16.435080] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [   16.435084] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [   16.435196] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [   16.435199] ov51x_jpeg: Unknown symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [   16.893798] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 14 18:30:55 Kubuntu kernel: [   17.043577] usbcore: registered new interface driver snd-usb-audio
Nov 14 18:30:55 Kubuntu kernel: [   17.084953] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [   17.084961] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [   17.085699] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [   17.085702] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [   17.085972] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [   17.085975] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [   17.086107] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [   17.086110] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [   17.086570] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [   17.086573] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [   17.086685] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [   17.086688] ov51x_jpeg: Unknown symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [   17.774583] C-Media PCI 0000:03:0c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 14 18:30:55 Kubuntu kernel: [   18.104766] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
Nov 14 18:30:55 Kubuntu kernel: [   21.032491] lp0: using parport0 (interrupt-driven).
Nov 14 18:30:55 Kubuntu kernel: [   21.275349] Adding 907632k swap on /dev/sda10.  Priority:-1 extents:1 across:907632k
Nov 14 18:30:55 Kubuntu kernel: [   22.212935] EXT3 FS on sda9, internal journal
Nov 14 18:30:55 Kubuntu kernel: [   22.502666] device-mapper: uevent: version 1.0.3
Nov 14 18:30:55 Kubuntu kernel: [   22.504867] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
Nov 14 18:30:55 Kubuntu kernel: [   24.258738] type=1505 audit(1226687453.412:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3921
Nov 14 18:30:55 Kubuntu kernel: [   24.259131] type=1505 audit(1226687453.412:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3921
Nov 14 18:30:55 Kubuntu kernel: [   24.454305] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 14 18:30:55 Kubuntu kernel: [   25.312323] ACPI: WMI: Mapper loaded
Nov 14 18:30:56 Kubuntu kernel: [   26.877969] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Nov 14 18:30:56 Kubuntu kernel: [   26.959346] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov 14 18:30:56 Kubuntu kernel: [   26.959359] apm: overridden by ACPI.
Nov 14 18:30:56 Kubuntu kernel: [   27.366407] ppdev: user-space parallel port driver
Nov 14 18:31:00 Kubuntu kernel: [   31.157280] NET: Registered protocol family 10
Nov 14 18:31:00 Kubuntu kernel: [   31.160208] lo: Disabled Privacy Extensions
Nov 14 18:31:02 Kubuntu kernel: [   33.676906] Bluetooth: Core ver 2.13
Nov 14 18:31:02 Kubuntu kernel: [   33.680044] NET: Registered protocol family 31
Nov 14 18:31:02 Kubuntu kernel: [   33.680056] Bluetooth: HCI device and connection manager initialized
Nov 14 18:31:02 Kubuntu kernel: [   33.680061] Bluetooth: HCI socket layer initialized
Nov 14 18:31:02 Kubuntu kernel: [   33.702339] Bluetooth: L2CAP ver 2.11
Nov 14 18:31:02 Kubuntu kernel: [   33.702352] Bluetooth: L2CAP socket layer initialized
Nov 14 18:31:02 Kubuntu kernel: [   33.720600] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 14 18:31:02 Kubuntu kernel: [   33.720611] Bluetooth: BNEP filters: protocol multicast
Nov 14 18:31:02 Kubuntu kernel: [   33.758416] Bridge firewalling registered
Nov 14 18:31:02 Kubuntu kernel: [   33.759722] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Nov 14 18:31:02 Kubuntu kernel: [   33.773794] Bluetooth: SCO (Voice Link) ver 0.6
Nov 14 18:31:02 Kubuntu kernel: [   33.773808] Bluetooth: SCO socket layer initialized
Nov 14 18:31:02 Kubuntu kernel: [   33.829595] Bluetooth: RFCOMM socket layer initialized
Nov 14 18:31:02 Kubuntu kernel: [   33.830949] Bluetooth: RFCOMM TTY layer initialized
Nov 14 18:31:02 Kubuntu kernel: [   33.830962] Bluetooth: RFCOMM ver 1.10
Nov 14 18:31:04 Kubuntu kernel: [   35.757205] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Nov 14 18:31:06 Kubuntu kernel: [   37.686172] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Nov 14 18:31:06 Kubuntu kernel: [   37.686222] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Nov 14 18:31:06 Kubuntu kernel: [   37.686264] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode
Nov 14 18:31:06 Kubuntu kernel: [   37.686302] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Nov 14 18:31:07 Kubuntu kernel: [   37.692194] [fglrx] Setup AGP aperture
Nov 14 18:31:07 Kubuntu kernel: [   37.950949] [fglrx] CMM init INV FB MC:0xb0000000, length:0x10000000
Nov 14 18:31:07 Kubuntu kernel: [   37.950985] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov 14 18:31:07 Kubuntu kernel: [   37.950989] [fglrx] Reserved FB block: Unshared offset:ff80000, size:80000 
Nov 14 18:31:07 Kubuntu kernel: [   37.985769] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 14 18:31:07 Kubuntu kernel: [   38.009673] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Nov 14 18:31:07 Kubuntu kernel: [   38.009946] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 14 18:31:07 Kubuntu kernel: [   38.202937] NET: Registered protocol family 17
Nov 14 18:31:12 Kubuntu kernel: [   48.328009] eth0: no IPv6 routers present
Nov 14 18:33:08 Kubuntu kernel: [  164.608187] ppdev0: registered pardevice
Nov 14 18:33:08 Kubuntu kernel: [  164.656081] ppdev0: unregistered pardevice
Nov 14 18:33:10 Kubuntu kernel: [  166.464396] ppdev0: registered pardevice
Nov 14 18:33:10 Kubuntu kernel: [  166.512331] ppdev0: unregistered pardevice
Nov 14 18:33:10 Kubuntu kernel: [  166.553505] ppdev0: registered pardevice
Nov 14 18:33:10 Kubuntu kernel: [  166.600776] ppdev0: unregistered pardevice


---

### Post by linux23dragon on 2008-11-15
> **socngill said:**
> Here it is (it's quite long...)


That does not look good.  The following part of your log says that its disagrees about version of symbol video_unregister_device.

Can you remove the option ***ov51x forceblock=1*** that you added into  [I][B]/etc/modprobe.d/options
[/B][/I] please?

This is your current error in the kernel log :-

```
Nov 14 18:30:55 Kubuntu kernel: [ 16.354319] Linux video capture interface: v2.00
Nov 14 18:30:55 Kubuntu kernel: [ 16.428607] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 16.428613] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 16.429266] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.429270] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.429505] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 16.429508] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 16.429626] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.429629] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.430046] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 16.430048] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 16.430148] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 16.430151] ov51x_jpeg: Unknown symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 16.433657] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 16.433666] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 16.434310] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.434314] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.434547] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 16.434551] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 16.434668] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.434671] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 16.435080] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 16.435084] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 16.435196] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 16.435199] ov51x_jpeg: Unknown symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 16.893798] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 14 18:30:55 Kubuntu kernel: [ 17.043577] usbcore: registered new interface driver snd-usb-audio
Nov 14 18:30:55 Kubuntu kernel: [ 17.084953] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 17.084961] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 17.085699] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.085702] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.085972] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 17.085975] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 17.086107] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.086110] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.086570] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 17.086573] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 17.086685] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 17.086688] ov51x_jpeg: Unknown symbol video_device_release

=====/cut=======

Nov 14 18:33:08 Kubuntu kernel: [ 164.608187] ppdev0: registered pardevice
Nov 14 18:33:08 Kubuntu kernel: [ 164.656081] ppdev0: unregistered pardevice
Nov 14 18:33:10 Kubuntu kernel: [ 166.464396] ppdev0: registered pardevice
Nov 14 18:33:10 Kubuntu kernel: [ 166.512331] ppdev0: unregistered pardevice
Nov 14 18:33:10 Kubuntu kernel: [ 166.553505] ppdev0: registered pardevice
Nov 14 18:33:10 Kubuntu kernel: [ 166.600776] ppdev0: unregistered pardevice 
```


Then post the new kernel log (after rebooting)

---

### Post by socngill on 2008-11-17
> Then post the new kernel log (after rebooting)

As reqwuested.  Still seems to be showing error messages.

> Nov 17 08:33:07 Kubuntu kernel: [  653.302124] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:07 Kubuntu kernel: [  653.302140] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:07 Kubuntu kernel: [  653.302147] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:07 Kubuntu kernel: [  653.302154] end_request: I/O error, dev sr0, sector 1257592
Nov 17 08:33:07 Kubuntu kernel: [  653.302162] Buffer I/O error on device sr0, logical block 157199
Nov 17 08:33:07 Kubuntu kernel: [  653.302169] Buffer I/O error on device sr0, logical block 157200
Nov 17 08:33:07 Kubuntu kernel: [  653.302173] Buffer I/O error on device sr0, logical block 157201
Nov 17 08:33:07 Kubuntu kernel: [  653.302177] Buffer I/O error on device sr0, logical block 157202
Nov 17 08:33:07 Kubuntu kernel: [  653.302181] Buffer I/O error on device sr0, logical block 157203
Nov 17 08:33:07 Kubuntu kernel: [  653.302185] Buffer I/O error on device sr0, logical block 157204
Nov 17 08:33:07 Kubuntu kernel: [  653.302189] Buffer I/O error on device sr0, logical block 157205
Nov 17 08:33:07 Kubuntu kernel: [  653.302193] Buffer I/O error on device sr0, logical block 157206
Nov 17 08:33:07 Kubuntu kernel: [  653.302197] Buffer I/O error on device sr0, logical block 157207
Nov 17 08:33:07 Kubuntu kernel: [  653.302201] Buffer I/O error on device sr0, logical block 157208
Nov 17 08:33:12 Kubuntu kernel: [  658.284456] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:12 Kubuntu kernel: [  658.284474] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:12 Kubuntu kernel: [  658.284480] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:12 Kubuntu kernel: [  658.284488] end_request: I/O error, dev sr0, sector 1257848
Nov 17 08:33:30 Kubuntu kernel: [  676.780120] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:30 Kubuntu kernel: [  676.780134] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:30 Kubuntu kernel: [  676.780140] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:30 Kubuntu kernel: [  676.780147] end_request: I/O error, dev sr0, sector 1266944
Nov 17 08:33:30 Kubuntu kernel: [  676.780155] __ratelimit: 54 callbacks suppressed
Nov 17 08:33:30 Kubuntu kernel: [  676.780159] Buffer I/O error on device sr0, logical block 158368
Nov 17 08:33:31 Kubuntu kernel: [  677.538482] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:31 Kubuntu kernel: [  677.538498] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:31 Kubuntu kernel: [  677.538504] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:31 Kubuntu kernel: [  677.538512] end_request: I/O error, dev sr0, sector 1267768
Nov 17 08:33:31 Kubuntu kernel: [  677.538521] Buffer I/O error on device sr0, logical block 158471
Nov 17 08:33:32 Kubuntu kernel: [  678.241739] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:32 Kubuntu kernel: [  678.241755] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:32 Kubuntu kernel: [  678.241761] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:32 Kubuntu kernel: [  678.241768] end_request: I/O error, dev sr0, sector 1267768
Nov 17 08:33:32 Kubuntu kernel: [  678.241777] Buffer I/O error on device sr0, logical block 158471
Nov 17 08:33:32 Kubuntu kernel: [  678.935424] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:32 Kubuntu kernel: [  678.935442] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:32 Kubuntu kernel: [  678.935449] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:32 Kubuntu kernel: [  678.935456] end_request: I/O error, dev sr0, sector 1267768
Nov 17 08:33:32 Kubuntu kernel: [  678.935466] Buffer I/O error on device sr0, logical block 158471
Nov 17 08:33:37 Kubuntu kernel: [  683.700271] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:37 Kubuntu kernel: [  683.700286] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:37 Kubuntu kernel: [  683.700293] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:37 Kubuntu kernel: [  683.700299] end_request: I/O error, dev sr0, sector 1273464
Nov 17 08:33:37 Kubuntu kernel: [  683.700308] Buffer I/O error on device sr0, logical block 159183
Nov 17 08:33:42 Kubuntu kernel: [  688.445119] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:42 Kubuntu kernel: [  688.445134] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:42 Kubuntu kernel: [  688.445140] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:42 Kubuntu kernel: [  688.445147] end_request: I/O error, dev sr0, sector 1273464
Nov 17 08:33:42 Kubuntu kernel: [  688.445155] Buffer I/O error on device sr0, logical block 159183
Nov 17 08:33:47 Kubuntu kernel: [  693.162795] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:47 Kubuntu kernel: [  693.162808] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:47 Kubuntu kernel: [  693.162815] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:47 Kubuntu kernel: [  693.162822] end_request: I/O error, dev sr0, sector 1273464
Nov 17 08:33:47 Kubuntu kernel: [  693.162830] Buffer I/O error on device sr0, logical block 159183
Nov 17 08:33:51 Kubuntu kernel: [  697.931230] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:51 Kubuntu kernel: [  697.931245] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:51 Kubuntu kernel: [  697.931251] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:51 Kubuntu kernel: [  697.931257] end_request: I/O error, dev sr0, sector 1275432
Nov 17 08:33:51 Kubuntu kernel: [  697.931266] Buffer I/O error on device sr0, logical block 159429
Nov 17 08:33:56 Kubuntu kernel: [  702.681838] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:33:56 Kubuntu kernel: [  702.681853] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:33:56 Kubuntu kernel: [  702.681859] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:33:56 Kubuntu kernel: [  702.681867] end_request: I/O error, dev sr0, sector 1275432
Nov 17 08:33:56 Kubuntu kernel: [  702.681877] Buffer I/O error on device sr0, logical block 159429
Nov 17 08:34:01 Kubuntu kernel: [  707.477333] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:01 Kubuntu kernel: [  707.477347] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:01 Kubuntu kernel: [  707.477353] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:01 Kubuntu kernel: [  707.477360] end_request: I/O error, dev sr0, sector 1275432
Nov 17 08:34:01 Kubuntu kernel: [  707.477369] Buffer I/O error on device sr0, logical block 159429
Nov 17 08:34:06 Kubuntu kernel: [  712.287337] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:06 Kubuntu kernel: [  712.287351] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:06 Kubuntu kernel: [  712.287357] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:06 Kubuntu kernel: [  712.287364] end_request: I/O error, dev sr0, sector 1278984
Nov 17 08:34:06 Kubuntu kernel: [  712.287372] Buffer I/O error on device sr0, logical block 159873
Nov 17 08:34:10 Kubuntu kernel: [  716.820584] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:10 Kubuntu kernel: [  716.820600] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:10 Kubuntu kernel: [  716.820607] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:10 Kubuntu kernel: [  716.820614] end_request: I/O error, dev sr0, sector 1278984
Nov 17 08:34:10 Kubuntu kernel: [  716.820624] Buffer I/O error on device sr0, logical block 159873
Nov 17 08:34:15 Kubuntu kernel: [  721.375336] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:15 Kubuntu kernel: [  721.375353] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:15 Kubuntu kernel: [  721.375359] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:15 Kubuntu kernel: [  721.375366] end_request: I/O error, dev sr0, sector 1278984
Nov 17 08:34:15 Kubuntu kernel: [  721.375376] Buffer I/O error on device sr0, logical block 159873
Nov 17 08:34:16 Kubuntu kernel: [  722.071129] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:16 Kubuntu kernel: [  722.071144] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:16 Kubuntu kernel: [  722.071150] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:16 Kubuntu kernel: [  722.071158] end_request: I/O error, dev sr0, sector 1288728
Nov 17 08:34:16 Kubuntu kernel: [  722.071169] Buffer I/O error on device sr0, logical block 161091
Nov 17 08:34:16 Kubuntu kernel: [  722.672760] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:16 Kubuntu kernel: [  722.672775] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:16 Kubuntu kernel: [  722.672782] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:16 Kubuntu kernel: [  722.672789] end_request: I/O error, dev sr0, sector 1288728
Nov 17 08:34:16 Kubuntu kernel: [  722.672798] Buffer I/O error on device sr0, logical block 161091
Nov 17 08:34:17 Kubuntu kernel: [  723.351134] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:17 Kubuntu kernel: [  723.351149] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:17 Kubuntu kernel: [  723.351155] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:17 Kubuntu kernel: [  723.351162] end_request: I/O error, dev sr0, sector 1288728
Nov 17 08:34:17 Kubuntu kernel: [  723.351171] Buffer I/O error on device sr0, logical block 161091
Nov 17 08:34:17 Kubuntu kernel: [  723.838460] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:17 Kubuntu kernel: [  723.838475] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:17 Kubuntu kernel: [  723.838482] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:17 Kubuntu kernel: [  723.838489] end_request: I/O error, dev sr0, sector 1288728
Nov 17 08:34:17 Kubuntu kernel: [  723.838497] Buffer I/O error on device sr0, logical block 161091
Nov 17 08:34:18 Kubuntu kernel: [  724.369535] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:18 Kubuntu kernel: [  724.369550] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:18 Kubuntu kernel: [  724.369556] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:18 Kubuntu kernel: [  724.369563] end_request: I/O error, dev sr0, sector 1288728
Nov 17 08:34:18 Kubuntu kernel: [  724.369573] Buffer I/O error on device sr0, logical block 161091
Nov 17 08:34:18 Kubuntu kernel: [  724.924034] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:18 Kubuntu kernel: [  724.924049] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:18 Kubuntu kernel: [  724.924055] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:18 Kubuntu kernel: [  724.924062] end_request: I/O error, dev sr0, sector 1288728
Nov 17 08:34:18 Kubuntu kernel: [  724.924071] Buffer I/O error on device sr0, logical block 161091
Nov 17 08:34:19 Kubuntu kernel: [  725.694684] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:19 Kubuntu kernel: [  725.694702] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:19 Kubuntu kernel: [  725.694708] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:19 Kubuntu kernel: [  725.694715] end_request: I/O error, dev sr0, sector 1292160
Nov 17 08:34:19 Kubuntu kernel: [  725.694724] Buffer I/O error on device sr0, logical block 161520
Nov 17 08:34:20 Kubuntu kernel: [  726.279017] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:20 Kubuntu kernel: [  726.279031] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:20 Kubuntu kernel: [  726.279038] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:20 Kubuntu kernel: [  726.279044] end_request: I/O error, dev sr0, sector 1292208
Nov 17 08:34:20 Kubuntu kernel: [  726.279053] Buffer I/O error on device sr0, logical block 161526
Nov 17 08:34:20 Kubuntu kernel: [  726.892739] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:20 Kubuntu kernel: [  726.892753] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:20 Kubuntu kernel: [  726.892759] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:20 Kubuntu kernel: [  726.892766] end_request: I/O error, dev sr0, sector 1292208
Nov 17 08:34:20 Kubuntu kernel: [  726.892774] Buffer I/O error on device sr0, logical block 161526
Nov 17 08:34:21 Kubuntu kernel: [  727.516389] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:21 Kubuntu kernel: [  727.516407] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:21 Kubuntu kernel: [  727.516413] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:21 Kubuntu kernel: [  727.516420] end_request: I/O error, dev sr0, sector 1292208
Nov 17 08:34:21 Kubuntu kernel: [  727.516428] Buffer I/O error on device sr0, logical block 161526
Nov 17 08:34:22 Kubuntu kernel: [  728.420913] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 08:34:22 Kubuntu kernel: [  728.420928] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 08:34:22 Kubuntu kernel: [  728.420934] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 08:34:22 Kubuntu kernel: [  728.420941] end_request: I/O error, dev sr0, sector 1307392
Nov 17 08:34:22 Kubuntu kernel: [  728.420950] Buffer I/O error on device sr0, logical block 163424
Nov 17 18:04:36 Kubuntu kernel: [34942.752178] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 17 18:05:38 Kubuntu kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov 17 18:05:38 Kubuntu kernel: Cannot find map file.
Nov 17 18:05:38 Kubuntu kernel: Loaded 55959 symbols from 101 modules.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000004ff30000 (usable)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000004ff30000 - 000000004ff40000 (ACPI data)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000004ff40000 - 000000004fff0000 (ACPI NVS)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 000000004fff0000 - 0000000050000000 (reserved)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] last_pfn = 0x4ff30 max_arch_pfn = 0x100000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] RAMDISK: 377cd000 - 37fef9e1
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] DMI 2.3 present.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: RSDP 000F9E30, 0014 (r0 ACPIAM)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: RSDT 4FF30000, 0030 (r1 A M I  OEMRSDT   7000422 MSFT       97)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: FACP 4FF30200, 0081 (r2 A M I  OEMFACP   7000422 MSFT       97)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: DSDT 4FF303F0, 3797 (r1  P4CED P4CED105      105 INTL  2002026)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: FACS 4FF40000, 0040
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: APIC 4FF30390, 005C (r1 A M I  OEMAPIC   7000422 MSFT       97)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: OEMB 4FF40040, 003F (r1 A M I  OEMBIOS   7000422 MSFT       97)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] 383MB HIGHMEM available.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] 896MB LOWMEM available.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   mapped low ram: 0 - 38000000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   low ram: 00000000 - 38000000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   bootmap 00008000 - 0000f000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #4 [00377cd000 - 0037fef9e1]          RAMDISK ==> [00377cd000 - 0037fef9e1]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] found SMP MP-table at [c00ff780] 000ff780
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Zone PFN ranges:
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   HighMem  0x00038000 -> 0x0004ff30
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Movable zone start PFN for each node
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0004ff30
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] On node 0 totalpages: 327375
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Nov 17 18:05:38 Kubuntu kernel: [    0.000000]   HighMem zone: 97233 pages, LIFO batch:31
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:afb80000)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324496
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Kernel command line: root=UUID=ffa383af-0850-4dc3-adcf-4bd02067816c ro quiet splash
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Initializing CPU#0
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] TSC: using PMTIMER calibration value
Nov 17 18:05:38 Kubuntu kernel: [    0.000000] Detected 2665.342 MHz processor.
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] Console: colour VGA+ 80x25
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] console [tty0] enabled
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] Memory: 1282924k/1309888k available (2572k kernel code, 25664k reserved, 1160k data, 424k init, 392384k highmem)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] virtual kernel memory layout:
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Nov 17 18:05:38 Kubuntu kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 17 18:05:38 Kubuntu kernel: [    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 5330.68 BogoMIPS (lpj=10661368)
Nov 17 18:05:38 Kubuntu kernel: [    0.004047] Security Framework initialized
Nov 17 18:05:38 Kubuntu kernel: [    0.004059] SELinux:  Disabled at boot.
Nov 17 18:05:38 Kubuntu kernel: [    0.004091] AppArmor: AppArmor initialized
Nov 17 18:05:38 Kubuntu kernel: [    0.004108] Mount-cache hash table entries: 512
Nov 17 18:05:38 Kubuntu kernel: [    0.004358] Initializing cgroup subsys ns
Nov 17 18:05:38 Kubuntu kernel: [    0.004367] Initializing cgroup subsys cpuacct
Nov 17 18:05:38 Kubuntu kernel: [    0.004370] Initializing cgroup subsys memory
Nov 17 18:05:38 Kubuntu kernel: [    0.004397] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov 17 18:05:38 Kubuntu kernel: [    0.004401] CPU: L2 cache: 256K
Nov 17 18:05:38 Kubuntu kernel: [    0.004404] CPU: Hyper-Threading is disabled
Nov 17 18:05:38 Kubuntu kernel: [    0.004410] using mwait in idle threads.
Nov 17 18:05:38 Kubuntu kernel: [    0.004428] Checking 'hlt' instruction... OK.
Nov 17 18:05:38 Kubuntu kernel: [    0.020696] SMP alternatives: switching to UP code
Nov 17 18:05:38 Kubuntu kernel: [    0.031131] ACPI: Core revision 20080609
Nov 17 18:05:38 Kubuntu kernel: [    0.033458] ACPI: Checking initramfs for custom DSDT
Nov 17 18:05:38 Kubuntu kernel: [    0.408559] ENABLING IO-APIC IRQs
Nov 17 18:05:38 Kubuntu kernel: [    0.408742] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 17 18:05:38 Kubuntu kernel: [    0.448436] CPU0: Intel(R) Celeron(R) CPU 2.66GHz stepping 01
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] Brought up 1 CPUs
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] Total of 1 processors activated (5330.68 BogoMIPS).
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] CPU0 attaching sched-domain:
Nov 17 18:05:38 Kubuntu kernel: [    0.452028]  domain 0: span 0 level CPU
Nov 17 18:05:38 Kubuntu kernel: [    0.452028]   groups: 0
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] net_namespace: 840 bytes
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] Booting paravirtualized kernel on bare hardware
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] Time: 18:05:12  Date: 11/17/08
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] NET: Registered protocol family 16
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] EISA bus registered
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] ACPI: bus type pci registered
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
Nov 17 18:05:38 Kubuntu kernel: [    0.452028] PCI: Using configuration type 1 for base access
Nov 17 18:05:38 Kubuntu kernel: [    0.452683] ACPI: EC: Look up EC in DSDT
Nov 17 18:05:38 Kubuntu kernel: [    0.463753] ACPI: Interpreter enabled
Nov 17 18:05:38 Kubuntu kernel: [    0.463760] ACPI: (supports S0 S1 S3 S4 S5)
Nov 17 18:05:38 Kubuntu kernel: [    0.463788] ACPI: Using IOAPIC for interrupt routing
Nov 17 18:05:38 Kubuntu kernel: [    0.479593] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 17 18:05:38 Kubuntu kernel: [    0.479751] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, efffffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.479929] PCI: 0000:00:1d.0 reg 20 io port: [eec0, eedf]
Nov 17 18:05:38 Kubuntu kernel: [    0.479986] PCI: 0000:00:1d.1 reg 20 io port: [ef00, ef1f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480060] PCI: 0000:00:1d.2 reg 20 io port: [ef20, ef3f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480118] PCI: 0000:00:1d.3 reg 20 io port: [ef40, ef5f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480184] PCI: 0000:00:1d.7 reg 10 32bit mmio: [febff800, febffbff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480242] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Nov 17 18:05:38 Kubuntu kernel: [    0.480248] pci 0000:00:1d.7: PME# disabled
Nov 17 18:05:38 Kubuntu kernel: [    0.480341] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Nov 17 18:05:38 Kubuntu kernel: [    0.480350] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Nov 17 18:05:38 Kubuntu kernel: [    0.480355] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Nov 17 18:05:38 Kubuntu kernel: [    0.480377] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
Nov 17 18:05:38 Kubuntu kernel: [    0.480385] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
Nov 17 18:05:38 Kubuntu kernel: [    0.480393] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
Nov 17 18:05:38 Kubuntu kernel: [    0.480401] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
Nov 17 18:05:38 Kubuntu kernel: [    0.480409] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480417] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480471] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480549] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480558] PCI: 0000:01:00.0 reg 14 io port: [b000, b0ff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480566] PCI: 0000:01:00.0 reg 18 32bit mmio: [fe8f0000, fe8fffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480589] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe8c0000, fe8dffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480612] pci 0000:01:00.0: supports D1
Nov 17 18:05:38 Kubuntu kernel: [    0.480614] pci 0000:01:00.0: supports D2
Nov 17 18:05:38 Kubuntu kernel: [    0.480646] PCI: 0000:01:00.1 reg 10 32bit mmio: [fe8e0000, fe8effff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480693] pci 0000:01:00.1: supports D1
Nov 17 18:05:38 Kubuntu kernel: [    0.480695] pci 0000:01:00.1: supports D2
Nov 17 18:05:38 Kubuntu kernel: [    0.480740] PCI: bridge 0000:00:01.0 io port: [b000, bfff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480744] PCI: bridge 0000:00:01.0 32bit mmio: [fe800000, fe8fffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480749] PCI: bridge 0000:00:01.0 32bit mmio pref: [bff00000, dfefffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480786] PCI: 0000:02:01.0 reg 10 32bit mmio: [fe9e0000, fe9fffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480798] PCI: 0000:02:01.0 reg 18 io port: [cf80, cf9f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480830] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
Nov 17 18:05:38 Kubuntu kernel: [    0.480835] pci 0000:02:01.0: PME# disabled
Nov 17 18:05:38 Kubuntu kernel: [    0.480873] PCI: bridge 0000:00:03.0 io port: [c000, cfff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480878] PCI: bridge 0000:00:03.0 32bit mmio: [fe900000, fe9fffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480923] PCI: 0000:03:03.0 reg 10 32bit mmio: [feaff800, feafffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.480931] PCI: 0000:03:03.0 reg 14 io port: [dc00, dc7f]
Nov 17 18:05:38 Kubuntu kernel: [    0.480973] pci 0000:03:03.0: supports D2
Nov 17 18:05:38 Kubuntu kernel: [    0.480975] pci 0000:03:03.0: PME# supported from D2 D3hot D3cold
Nov 17 18:05:38 Kubuntu kernel: [    0.480980] pci 0000:03:03.0: PME# disabled
Nov 17 18:05:38 Kubuntu kernel: [    0.481022] PCI: 0000:03:0c.0 reg 10 io port: [d800, d8ff]
Nov 17 18:05:38 Kubuntu kernel: [    0.481068] pci 0000:03:0c.0: supports D1
Nov 17 18:05:38 Kubuntu kernel: [    0.481070] pci 0000:03:0c.0: supports D2
Nov 17 18:05:38 Kubuntu kernel: [    0.481097] pci 0000:00:1e.0: transparent bridge
Nov 17 18:05:38 Kubuntu kernel: [    0.481102] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
Nov 17 18:05:38 Kubuntu kernel: [    0.481108] PCI: bridge 0000:00:1e.0 32bit mmio: [fea00000, feafffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.481129] bus 00 -> node 0
Nov 17 18:05:38 Kubuntu kernel: [    0.481143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 17 18:05:38 Kubuntu kernel: [    0.481388] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov 17 18:05:38 Kubuntu kernel: [    0.481839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
Nov 17 18:05:38 Kubuntu kernel: [    0.493287] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 17 18:05:38 Kubuntu kernel: [    0.493476] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 17 18:05:38 Kubuntu kernel: [    0.493660] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 17 18:05:38 Kubuntu kernel: [    0.493845] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 17 18:05:38 Kubuntu kernel: [    0.494031] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 17 18:05:38 Kubuntu kernel: [    0.494217] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 17 18:05:38 Kubuntu kernel: [    0.494405] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 17 18:05:38 Kubuntu kernel: [    0.494592] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov 17 18:05:38 Kubuntu kernel: [    0.494961] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - EE, should be DF [20080609]
Nov 17 18:05:38 Kubuntu kernel: [    0.494975] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 17 18:05:38 Kubuntu kernel: [    0.495068] pnp: PnP ACPI init
Nov 17 18:05:38 Kubuntu kernel: [    0.495085] ACPI: bus type pnp registered
Nov 17 18:05:38 Kubuntu kernel: [    0.504402] pnp: PnP ACPI: found 15 devices
Nov 17 18:05:38 Kubuntu kernel: [    0.504408] ACPI: ACPI bus type pnp unregistered
Nov 17 18:05:38 Kubuntu kernel: [    0.504415] PnPBIOS: Disabled by ACPI PNP
Nov 17 18:05:38 Kubuntu kernel: [    0.505239] PCI: Using ACPI for IRQ routing
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] NET: Registered protocol family 8
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] NET: Registered protocol family 20
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] NetLabel: Initializing
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] NetLabel:  domain hash size = 128
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] NetLabel:  unlabeled traffic allowed by default
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] hpet clockevent registered
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 17 18:05:38 Kubuntu kernel: [    0.505451] hpet0: 3 64-bit timers, 14318180 Hz
Nov 17 18:05:38 Kubuntu kernel: [    0.505963] tracer: 772 pages allocated for 65536 entries of 48 bytes
Nov 17 18:05:38 Kubuntu kernel: [    0.505967]    actual entries 65620
Nov 17 18:05:38 Kubuntu kernel: [    0.506179] AppArmor: AppArmor Filesystem Enabled
Nov 17 18:05:38 Kubuntu kernel: [    0.506209] ACPI: RTC can wake from S4
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0b: ioport range 0x680-0x6ff has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0b: ioport range 0x290-0x297 has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0c: ioport range 0x800-0x87f has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0c: ioport range 0x480-0x4bf has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0c: iomem range 0xffb00000-0xffbfffff could not be reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0e: iomem range 0x100000-0x4ffeffff could not be reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.506250] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
Nov 17 18:05:38 Kubuntu kernel: [    0.543573] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov 17 18:05:38 Kubuntu kernel: [    0.543580] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
Nov 17 18:05:38 Kubuntu kernel: [    0.543587] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe8fffff
Nov 17 18:05:38 Kubuntu kernel: [    0.543592] pci 0000:00:01.0:   PREFETCH window: 0x000000bff00000-0x000000dfefffff
Nov 17 18:05:38 Kubuntu kernel: [    0.543600] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
Nov 17 18:05:38 Kubuntu kernel: [    0.543604] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
Nov 17 18:05:38 Kubuntu kernel: [    0.543611] pci 0000:00:03.0:   MEM window: 0xfe900000-0xfe9fffff
Nov 17 18:05:38 Kubuntu kernel: [    0.543615] pci 0000:00:03.0:   PREFETCH window: disabled
Nov 17 18:05:38 Kubuntu kernel: [    0.543623] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Nov 17 18:05:38 Kubuntu kernel: [    0.543627] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
Nov 17 18:05:38 Kubuntu kernel: [    0.543634] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
Nov 17 18:05:38 Kubuntu kernel: [    0.543639] pci 0000:00:1e.0:   PREFETCH window: disabled
Nov 17 18:05:38 Kubuntu kernel: [    0.543667] pci 0000:00:1e.0: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    0.543673] bus: 00 index 0 io port: [0, ffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543676] bus: 00 index 1 mmio: [0, ffffffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543679] bus: 01 index 0 io port: [b000, bfff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543681] bus: 01 index 1 mmio: [fe800000, fe8fffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543684] bus: 01 index 2 mmio: [bff00000, dfefffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543687] bus: 01 index 3 mmio: [0, 0]
Nov 17 18:05:38 Kubuntu kernel: [    0.543689] bus: 02 index 0 io port: [c000, cfff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543692] bus: 02 index 1 mmio: [fe900000, fe9fffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543694] bus: 02 index 2 mmio: [0, 0]
Nov 17 18:05:38 Kubuntu kernel: [    0.543696] bus: 02 index 3 mmio: [0, 0]
Nov 17 18:05:38 Kubuntu kernel: [    0.543699] bus: 03 index 0 io port: [d000, dfff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543702] bus: 03 index 1 mmio: [fea00000, feafffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543704] bus: 03 index 2 mmio: [0, 0]
Nov 17 18:05:38 Kubuntu kernel: [    0.543707] bus: 03 index 3 io port: [0, ffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543709] bus: 03 index 4 mmio: [0, ffffffff]
Nov 17 18:05:38 Kubuntu kernel: [    0.543727] NET: Registered protocol family 2
Nov 17 18:05:38 Kubuntu kernel: [    0.543978] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    0.544466] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    0.545540] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    0.546132] TCP: Hash tables configured (established 131072 bind 65536)
Nov 17 18:05:38 Kubuntu kernel: [    0.546139] TCP reno registered
Nov 17 18:05:38 Kubuntu kernel: [    0.546372] NET: Registered protocol family 1
Nov 17 18:05:38 Kubuntu kernel: [    0.546566] checking if image is initramfs... it is
Nov 17 18:05:38 Kubuntu kernel: [    1.008083] Switched to high resolution mode on CPU 0
Nov 17 18:05:38 Kubuntu kernel: [    1.339434] Freeing initrd memory: 8330k freed
Nov 17 18:05:38 Kubuntu kernel: [    1.340913] audit: initializing netlink socket (disabled)
Nov 17 18:05:38 Kubuntu kernel: [    1.340936] type=2000 audit(1226945112.340:1): initialized
Nov 17 18:05:38 Kubuntu kernel: [    1.346901] highmem bounce pool size: 64 pages
Nov 17 18:05:38 Kubuntu kernel: [    1.346914] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov 17 18:05:38 Kubuntu kernel: [    1.350977] VFS: Disk quotas dquot_6.5.1
Nov 17 18:05:38 Kubuntu kernel: [    1.351171] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 17 18:05:38 Kubuntu kernel: [    1.351383] msgmni has been set to 1757
Nov 17 18:05:38 Kubuntu kernel: [    1.351629] io scheduler noop registered
Nov 17 18:05:38 Kubuntu kernel: [    1.351635] io scheduler anticipatory registered
Nov 17 18:05:38 Kubuntu kernel: [    1.351637] io scheduler deadline registered
Nov 17 18:05:38 Kubuntu kernel: [    1.351665] io scheduler cfq registered (default)
Nov 17 18:05:38 Kubuntu kernel: [    1.351772] pci 0000:01:00.0: Boot video device
Nov 17 18:05:38 Kubuntu kernel: [    1.352998] isapnp: Scanning for PnP cards...
Nov 17 18:05:38 Kubuntu kernel: [    1.704719] isapnp: No Plug & Play device found
Nov 17 18:05:38 Kubuntu kernel: [    1.824379] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Nov 17 18:05:38 Kubuntu kernel: [    1.824575] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 17 18:05:38 Kubuntu kernel: [    1.824974] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 17 18:05:38 Kubuntu kernel: [    1.826737] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 17 18:05:38 Kubuntu kernel: [    1.827618] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 17 18:05:38 Kubuntu kernel: [    1.831544] brd: module loaded
Nov 17 18:05:38 Kubuntu kernel: [    1.831691] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 17 18:05:38 Kubuntu kernel: [    1.831952] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 17 18:05:38 Kubuntu kernel: [    1.834991] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 17 18:05:38 Kubuntu kernel: [    1.835003] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 17 18:05:38 Kubuntu kernel: [    1.835999] mice: PS/2 mouse device common for all mice
Nov 17 18:05:38 Kubuntu kernel: [    1.836449] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Nov 17 18:05:38 Kubuntu kernel: [    1.836479] rtc0: alarms up to one month, hpet irqs
Nov 17 18:05:38 Kubuntu kernel: [    1.836755] EISA: Probing bus 0 at eisa.0
Nov 17 18:05:38 Kubuntu kernel: [    1.836798] EISA: Detected 0 cards.
Nov 17 18:05:38 Kubuntu kernel: [    1.836803] cpuidle: using governor ladder
Nov 17 18:05:38 Kubuntu kernel: [    1.836805] cpuidle: using governor menu
Nov 17 18:05:38 Kubuntu kernel: [    1.837562] TCP cubic registered
Nov 17 18:05:38 Kubuntu kernel: [    1.837613] Using IPI No-Shortcut mode
Nov 17 18:05:38 Kubuntu kernel: [    1.838391] registered taskstats version 1
Nov 17 18:05:38 Kubuntu kernel: [    1.838520]   Magic number: 0:730:89
Nov 17 18:05:38 Kubuntu kernel: [    1.838688] rtc_cmos 00:02: setting system clock to 2008-11-17 18:05:14 UTC (1226945114)
Nov 17 18:05:38 Kubuntu kernel: [    1.838693] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 17 18:05:38 Kubuntu kernel: [    1.838696] EDD information not available.
Nov 17 18:05:38 Kubuntu kernel: [    1.839183] Freeing unused kernel memory: 424k freed
Nov 17 18:05:38 Kubuntu kernel: [    1.839253] Write protecting the kernel text: 2576k
Nov 17 18:05:38 Kubuntu kernel: [    1.839293] Write protecting the kernel read-only data: 936k
Nov 17 18:05:38 Kubuntu kernel: [    1.869209] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 17 18:05:38 Kubuntu kernel: [    2.100889] fuse init (API version 7.9)
Nov 17 18:05:38 Kubuntu kernel: [    2.357601] processor ACPI0007:00: registered as cooling_device0
Nov 17 18:05:38 Kubuntu kernel: [    3.332606] usbcore: registered new interface driver usbfs
Nov 17 18:05:38 Kubuntu kernel: [    3.332648] usbcore: registered new interface driver hub
Nov 17 18:05:38 Kubuntu kernel: [    3.344444] Intel(R) PRO/1000 Network Driver - version 7.3.20-k3-NAPI
Nov 17 18:05:38 Kubuntu kernel: [    3.344450] Copyright (c) 1999-2006 Intel Corporation.
Nov 17 18:05:38 Kubuntu kernel: [    3.344510] e1000 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 17 18:05:38 Kubuntu kernel: [    3.344521] e1000 0000:02:01.0: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    3.355707] usbcore: registered new device driver usb
Nov 17 18:05:38 Kubuntu kernel: [    3.378051] USB Universal Host Controller Interface driver v3.0
Nov 17 18:05:38 Kubuntu kernel: [    3.400262] No dock devices found.
Nov 17 18:05:38 Kubuntu kernel: [    3.455923] SCSI subsystem initialized
Nov 17 18:05:38 Kubuntu kernel: [    3.510399] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0c:6e:b6:ea:56
Nov 17 18:05:38 Kubuntu kernel: [    3.578266] libata version 3.00 loaded.
Nov 17 18:05:38 Kubuntu kernel: [    3.774477] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Nov 17 18:05:38 Kubuntu kernel: [    3.774631] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 17 18:05:38 Kubuntu kernel: [    3.774645] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    3.774650] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 17 18:05:38 Kubuntu kernel: [    3.774725] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov 17 18:05:38 Kubuntu kernel: [    3.774763] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
Nov 17 18:05:38 Kubuntu kernel: [    3.775041] usb usb1: configuration #1 chosen from 1 choice
Nov 17 18:05:38 Kubuntu kernel: [    3.775091] hub 1-0:1.0: USB hub found
Nov 17 18:05:38 Kubuntu kernel: [    3.775104] hub 1-0:1.0: 2 ports detected
Nov 17 18:05:38 Kubuntu kernel: [    3.876609] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 17 18:05:38 Kubuntu kernel: [    3.876624] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    3.876629] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 17 18:05:38 Kubuntu kernel: [    3.876687] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov 17 18:05:38 Kubuntu kernel: [    3.876725] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ef00
Nov 17 18:05:38 Kubuntu kernel: [    3.876995] usb usb2: configuration #1 chosen from 1 choice
Nov 17 18:05:38 Kubuntu kernel: [    3.877043] hub 2-0:1.0: USB hub found
Nov 17 18:05:38 Kubuntu kernel: [    3.877058] hub 2-0:1.0: 2 ports detected
Nov 17 18:05:38 Kubuntu kernel: [    4.084586] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Nov 17 18:05:38 Kubuntu kernel: [    4.084609] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    4.084614] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 17 18:05:38 Kubuntu kernel: [    4.084674] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
Nov 17 18:05:38 Kubuntu kernel: [    4.088601] ehci_hcd 0000:00:1d.7: debug port 1
Nov 17 18:05:38 Kubuntu kernel: [    4.088610] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
Nov 17 18:05:38 Kubuntu kernel: [    4.088630] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff800
Nov 17 18:05:38 Kubuntu kernel: [    4.104060] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 17 18:05:38 Kubuntu kernel: [    4.104348] usb usb3: configuration #1 chosen from 1 choice
Nov 17 18:05:38 Kubuntu kernel: [    4.104398] hub 3-0:1.0: USB hub found
Nov 17 18:05:38 Kubuntu kernel: [    4.104416] hub 3-0:1.0: 8 ports detected
Nov 17 18:05:38 Kubuntu kernel: [    4.312551] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 17 18:05:38 Kubuntu kernel: [    4.312566] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    4.312572] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 17 18:05:38 Kubuntu kernel: [    4.312620] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Nov 17 18:05:38 Kubuntu kernel: [    4.312659] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
Nov 17 18:05:38 Kubuntu kernel: [    4.312915] usb usb4: configuration #1 chosen from 1 choice
Nov 17 18:05:38 Kubuntu kernel: [    4.312971] hub 4-0:1.0: USB hub found
Nov 17 18:05:38 Kubuntu kernel: [    4.312986] hub 4-0:1.0: 2 ports detected
Nov 17 18:05:38 Kubuntu kernel: [    4.416568] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 17 18:05:38 Kubuntu kernel: [    4.416583] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    4.416588] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov 17 18:05:38 Kubuntu kernel: [    4.416647] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Nov 17 18:05:38 Kubuntu kernel: [    4.416678] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
Nov 17 18:05:38 Kubuntu kernel: [    4.416940] usb usb5: configuration #1 chosen from 1 choice
Nov 17 18:05:38 Kubuntu kernel: [    4.416992] hub 5-0:1.0: USB hub found
Nov 17 18:05:38 Kubuntu kernel: [    4.417007] hub 5-0:1.0: 2 ports detected
Nov 17 18:05:38 Kubuntu kernel: [    4.521212] ata_piix 0000:00:1f.1: version 2.12
Nov 17 18:05:38 Kubuntu kernel: [    4.521230] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Nov 17 18:05:38 Kubuntu kernel: [    4.521240] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 17 18:05:38 Kubuntu kernel: [    4.521302] ata_piix 0000:00:1f.1: setting latency timer to 64
Nov 17 18:05:38 Kubuntu kernel: [    4.522825] scsi0 : ata_piix
Nov 17 18:05:38 Kubuntu kernel: [    4.523028] scsi1 : ata_piix
Nov 17 18:05:38 Kubuntu kernel: [    4.525648] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Nov 17 18:05:38 Kubuntu kernel: [    4.525653] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Nov 17 18:05:38 Kubuntu kernel: [    4.716294] ata1.01: HPA unlocked: 240119615 -> 240121728, native 240121728
Nov 17 18:05:38 Kubuntu kernel: [    4.716303] ata1.01: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
Nov 17 18:05:38 Kubuntu kernel: [    4.716307] ata1.01: 240121728 sectors, multi 16: LBA 
Nov 17 18:05:38 Kubuntu kernel: [    4.732448] ata1.01: configured for UDMA/100
Nov 17 18:05:38 Kubuntu kernel: [    4.856036] usb 2-1: new full speed USB device using uhci_hcd and address 2
Nov 17 18:05:38 Kubuntu kernel: [    4.888201] ata2.01: NODEV after polling detection
Nov 17 18:05:38 Kubuntu kernel: [    4.896942] ata2.00: ATAPI: NU      DVDRW DDW-081, BX32, max UDMA/33
Nov 17 18:05:38 Kubuntu kernel: [    4.914014] ata2.00: configured for UDMA/33
Nov 17 18:05:38 Kubuntu kernel: [    4.914205] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
Nov 17 18:05:38 Kubuntu kernel: [    4.920532] scsi 1:0:0:0: CD-ROM            NU       DVDRW DDW-081    BX32 PQ: 0 ANSI: 5
Nov 17 18:05:38 Kubuntu kernel: [    4.922811] ohci1394 0000:03:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 17 18:05:38 Kubuntu kernel: [    4.975599] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 17 18:05:38 Kubuntu kernel: [    5.064897] usb 2-1: configuration #1 chosen from 1 choice
Nov 17 18:05:38 Kubuntu kernel: [    5.085663] scsi 0:0:1:0: Attached scsi generic sg0 type 0
Nov 17 18:05:38 Kubuntu kernel: [    5.085780] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Nov 17 18:05:38 Kubuntu kernel: [    5.122373] Driver 'sd' needs updating - please use bus_type methods
Nov 17 18:05:38 Kubuntu kernel: [    5.125241] sd 0:0:1:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Nov 17 18:05:38 Kubuntu kernel: [    5.125276] sd 0:0:1:0: [sda] Write Protect is off
Nov 17 18:05:38 Kubuntu kernel: [    5.125280] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Nov 17 18:05:38 Kubuntu kernel: [    5.125332] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 17 18:05:38 Kubuntu kernel: [    5.125475] sd 0:0:1:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
Nov 17 18:05:38 Kubuntu kernel: [    5.125507] sd 0:0:1:0: [sda] Write Protect is off
Nov 17 18:05:38 Kubuntu kernel: [    5.125511] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Nov 17 18:05:38 Kubuntu kernel: [    5.125563] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 17 18:05:38 Kubuntu kernel: [    5.125570]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Nov 17 18:05:38 Kubuntu kernel: [    5.141344]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
Nov 17 18:05:38 Kubuntu kernel: [    5.241974] sd 0:0:1:0: [sda] Attached SCSI disk
Nov 17 18:05:38 Kubuntu kernel: [    5.256069] sr0: scsi3-mmc drive: 94x/62x writer cd/rw xa/form2 cdda tray
Nov 17 18:05:38 Kubuntu kernel: [    5.256078] Uniform CD-ROM driver Revision: 3.20
Nov 17 18:05:38 Kubuntu kernel: [    5.256228] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov 17 18:05:38 Kubuntu kernel: [    5.758832] PM: Starting manual resume from disk
Nov 17 18:05:38 Kubuntu kernel: [    5.758840] PM: Resume from partition 8:10
Nov 17 18:05:38 Kubuntu kernel: [    5.758843] PM: Checking hibernation image.
Nov 17 18:05:38 Kubuntu kernel: [    5.760062] PM: Resume from disk failed.
Nov 17 18:05:38 Kubuntu kernel: [    5.811364] kjournald starting.  Commit interval 5 seconds
Nov 17 18:05:38 Kubuntu kernel: [    5.811391] EXT3-fs: mounted filesystem with ordered data mode.
Nov 17 18:05:38 Kubuntu kernel: [    6.256197] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000033b54c]
Nov 17 18:05:38 Kubuntu kernel: [   13.066423] udevd version 124 started
Nov 17 18:05:38 Kubuntu kernel: [   13.879345] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 17 18:05:38 Kubuntu kernel: [   13.934089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 17 18:05:38 Kubuntu kernel: [   14.010189] EDAC MC: Ver: 2.1.0 Nov  4 2008
Nov 17 18:05:38 Kubuntu kernel: [   14.092741] EDAC i82875p: i82875p init one
Nov 17 18:05:38 Kubuntu kernel: [   14.092787] PCI: 0000:00:06.0 reg 10 32bit mmio: [fecf0000, fecf0fff]
Nov 17 18:05:38 Kubuntu kernel: [   14.093796] pci 0000:00:06.0: device not available because of BAR 0 [0xfecf0000-0xfecf0fff] collisions
Nov 17 18:05:38 Kubuntu kernel: [   14.093804] EDAC i82875p: i82875p_setup_overfl_dev(): Failed to enable overflow device
Nov 17 18:05:38 Kubuntu kernel: [   14.223200] Linux agpgart interface v0.103
Nov 17 18:05:38 Kubuntu kernel: [   14.287581] agpgart-intel 0000:00:00.0: Intel i875 Chipset
Nov 17 18:05:38 Kubuntu kernel: [   14.369119] iTCO_vendor_support: vendor-support=0
Nov 17 18:05:38 Kubuntu kernel: [   14.422635] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Nov 17 18:05:38 Kubuntu kernel: [   14.422981] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Nov 17 18:05:38 Kubuntu kernel: [   14.424932] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
Nov 17 18:05:38 Kubuntu kernel: [   14.425197] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov 17 18:05:38 Kubuntu kernel: [   14.538169] intel_rng: FWH not detected
Nov 17 18:05:38 Kubuntu kernel: [   14.596956] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov 17 18:05:38 Kubuntu kernel: [   14.612087] ACPI: Power Button (FF) [PWRF]
Nov 17 18:05:38 Kubuntu kernel: [   14.612303] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov 17 18:05:38 Kubuntu kernel: [   14.628036] ACPI: Power Button (CM) [PWRB]
Nov 17 18:05:38 Kubuntu kernel: [   15.356262] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 17 18:05:38 Kubuntu kernel: [   15.356369] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov 17 18:05:38 Kubuntu kernel: [   15.626019] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 17 18:05:38 Kubuntu kernel: [   15.954371] [fglrx] Maximum main memory to use for locked dma buffers: 1169 MBytes.
Nov 17 18:05:38 Kubuntu kernel: [   15.954594] [fglrx]   vendor: 1002 device: 71c1 count: 1
Nov 17 18:05:38 Kubuntu kernel: [   15.955059] [fglrx] ioport: bar 1, base 0xb000, size: 0x100
Nov 17 18:05:38 Kubuntu kernel: [   15.955081] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 17 18:05:38 Kubuntu kernel: [   15.955604] [fglrx] PAT is enabled successfully!
Nov 17 18:05:38 Kubuntu kernel: [   15.955649] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
Nov 17 18:05:38 Kubuntu kernel: [   16.394362] Linux video capture interface: v2.00
Nov 17 18:05:38 Kubuntu kernel: [   16.443878] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 17 18:05:38 Kubuntu kernel: [   16.443886] ov51x_jpeg: Unknown symbol video_devdata
Nov 17 18:05:38 Kubuntu kernel: [   16.444641] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 17 18:05:38 Kubuntu kernel: [   16.444646] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 17 18:05:38 Kubuntu kernel: [   16.444905] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 17 18:05:38 Kubuntu kernel: [   16.444908] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 17 18:05:38 Kubuntu kernel: [   16.445038] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 17 18:05:38 Kubuntu kernel: [   16.445041] ov51x_jpeg: Unknown symbol video_register_device
Nov 17 18:05:38 Kubuntu kernel: [   16.445494] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 17 18:05:38 Kubuntu kernel: [   16.445497] ov51x_jpeg: Unknown symbol video_usercopy
Nov 17 18:05:38 Kubuntu kernel: [   16.445607] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 17 18:05:38 Kubuntu kernel: [   16.445610] ov51x_jpeg: Unknown symbol video_device_release
Nov 17 18:05:38 Kubuntu kernel: [   16.448281] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 17 18:05:38 Kubuntu kernel: [   16.448288] ov51x_jpeg: Unknown symbol video_devdata
Nov 17 18:05:38 Kubuntu kernel: [   16.448936] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 17 18:05:38 Kubuntu kernel: [   16.448939] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 17 18:05:38 Kubuntu kernel: [   16.449171] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 17 18:05:38 Kubuntu kernel: [   16.449175] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 17 18:05:38 Kubuntu kernel: [   16.449292] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 17 18:05:38 Kubuntu kernel: [   16.449295] ov51x_jpeg: Unknown symbol video_register_device
Nov 17 18:05:38 Kubuntu kernel: [   16.449708] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 17 18:05:38 Kubuntu kernel: [   16.449711] ov51x_jpeg: Unknown symbol video_usercopy
Nov 17 18:05:38 Kubuntu kernel: [   16.449810] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 17 18:05:38 Kubuntu kernel: [   16.449813] ov51x_jpeg: Unknown symbol video_device_release
Nov 17 18:05:38 Kubuntu kernel: [   16.923573] usbcore: registered new interface driver snd-usb-audio
Nov 17 18:05:38 Kubuntu kernel: [   16.954393] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 17 18:05:38 Kubuntu kernel: [   16.971936] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 17 18:05:38 Kubuntu kernel: [   16.971944] ov51x_jpeg: Unknown symbol video_devdata
Nov 17 18:05:38 Kubuntu kernel: [   16.972735] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 17 18:05:38 Kubuntu kernel: [   16.972739] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 17 18:05:38 Kubuntu kernel: [   16.973013] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 17 18:05:38 Kubuntu kernel: [   16.973017] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 17 18:05:38 Kubuntu kernel: [   16.973153] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 17 18:05:38 Kubuntu kernel: [   16.973156] ov51x_jpeg: Unknown symbol video_register_device
Nov 17 18:05:38 Kubuntu kernel: [   16.973627] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 17 18:05:38 Kubuntu kernel: [   16.973630] ov51x_jpeg: Unknown symbol video_usercopy
Nov 17 18:05:38 Kubuntu kernel: [   16.973746] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 17 18:05:38 Kubuntu kernel: [   16.973749] ov51x_jpeg: Unknown symbol video_device_release
Nov 17 18:05:38 Kubuntu kernel: [   17.330226] C-Media PCI 0000:03:0c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 17 18:05:38 Kubuntu kernel: [   17.961755] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 18:05:38 Kubuntu kernel: [   17.961764] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 18:05:38 Kubuntu kernel: [   17.961770] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 18:05:38 Kubuntu kernel: [   17.961776] end_request: I/O error, dev sr0, sector 16679280
Nov 17 18:05:38 Kubuntu kernel: [   17.961785] Buffer I/O error on device sr0, logical block 2084910
Nov 17 18:05:38 Kubuntu kernel: [   18.042095] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 17 18:05:38 Kubuntu kernel: [   18.042103] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov 17 18:05:38 Kubuntu kernel: [   18.042109] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Nov 17 18:05:38 Kubuntu kernel: [   18.042116] end_request: I/O error, dev sr0, sector 16679280
Nov 17 18:05:38 Kubuntu kernel: [   18.042124] Buffer I/O error on device sr0, logical block 2084910
Nov 17 18:05:38 Kubuntu kernel: [   18.095686] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
Nov 17 18:05:38 Kubuntu kernel: [   21.028958] lp0: using parport0 (interrupt-driven).
Nov 17 18:05:38 Kubuntu kernel: [   21.273557] Adding 907632k swap on /dev/sda10.  Priority:-1 extents:1 across:907632k
Nov 17 18:05:38 Kubuntu kernel: [   22.209714] EXT3 FS on sda9, internal journal
Nov 17 18:05:38 Kubuntu kernel: [   22.501033] device-mapper: uevent: version 1.0.3
Nov 17 18:05:38 Kubuntu kernel: [   22.503170] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
Nov 17 18:05:38 Kubuntu kernel: [   24.273625] type=1505 audit(1226945136.432:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3918
Nov 17 18:05:38 Kubuntu kernel: [   24.274011] type=1505 audit(1226945136.432:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3918
Nov 17 18:05:38 Kubuntu kernel: [   24.477139] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 17 18:05:38 Kubuntu kernel: [   25.335416] ACPI: WMI: Mapper loaded
Nov 17 18:05:39 Kubuntu kernel: [   26.875261] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Nov 17 18:05:39 Kubuntu kernel: [   26.957019] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov 17 18:05:39 Kubuntu kernel: [   26.957032] apm: overridden by ACPI.
Nov 17 18:05:39 Kubuntu kernel: [   27.330790] ppdev: user-space parallel port driver
Nov 17 18:05:42 Kubuntu kernel: [   30.729951] NET: Registered protocol family 10
Nov 17 18:05:42 Kubuntu kernel: [   30.733005] lo: Disabled Privacy Extensions
Nov 17 18:05:45 Kubuntu kernel: [   33.066123] Bluetooth: Core ver 2.13
Nov 17 18:05:45 Kubuntu kernel: [   33.069408] NET: Registered protocol family 31
Nov 17 18:05:45 Kubuntu kernel: [   33.069418] Bluetooth: HCI device and connection manager initialized
Nov 17 18:05:45 Kubuntu kernel: [   33.069423] Bluetooth: HCI socket layer initialized
Nov 17 18:05:45 Kubuntu kernel: [   33.091640] Bluetooth: L2CAP ver 2.11
Nov 17 18:05:45 Kubuntu kernel: [   33.091652] Bluetooth: L2CAP socket layer initialized
Nov 17 18:05:45 Kubuntu kernel: [   33.109758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 17 18:05:45 Kubuntu kernel: [   33.109769] Bluetooth: BNEP filters: protocol multicast
Nov 17 18:05:45 Kubuntu kernel: [   33.176390] Bridge firewalling registered
Nov 17 18:05:45 Kubuntu kernel: [   33.177701] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Nov 17 18:05:45 Kubuntu kernel: [   33.191457] Bluetooth: SCO (Voice Link) ver 0.6
Nov 17 18:05:45 Kubuntu kernel: [   33.191472] Bluetooth: SCO socket layer initialized
Nov 17 18:05:45 Kubuntu kernel: [   33.233328] Bluetooth: RFCOMM socket layer initialized
Nov 17 18:05:45 Kubuntu kernel: [   33.233734] Bluetooth: RFCOMM TTY layer initialized
Nov 17 18:05:45 Kubuntu kernel: [   33.233747] Bluetooth: RFCOMM ver 1.10
Nov 17 18:05:47 Kubuntu kernel: [   35.164068] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Nov 17 18:05:49 Kubuntu kernel: [   37.017161] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Nov 17 18:05:49 Kubuntu kernel: [   37.017212] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Nov 17 18:05:49 Kubuntu kernel: [   37.017253] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode
Nov 17 18:05:49 Kubuntu kernel: [   37.017292] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Nov 17 18:05:49 Kubuntu kernel: [   37.023264] [fglrx] Setup AGP aperture
Nov 17 18:05:49 Kubuntu kernel: [   37.281631] [fglrx] CMM init INV FB MC:0xb0000000, length:0x10000000
Nov 17 18:05:49 Kubuntu kernel: [   37.281668] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov 17 18:05:49 Kubuntu kernel: [   37.281672] [fglrx] Reserved FB block: Unshared offset:ff80000, size:80000 
Nov 17 18:05:49 Kubuntu kernel: [   37.381726] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 17 18:05:49 Kubuntu kernel: [   37.405671] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Nov 17 18:05:49 Kubuntu kernel: [   37.405970] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 17 18:05:49 Kubuntu kernel: [   37.738580] NET: Registered protocol family 17
Nov 17 18:05:55 Kubuntu kernel: [   48.312018] eth0: no IPv6 routers present
Nov 17 19:47:32 Kubuntu kernel: [ 6145.309012] ppdev0: registered pardevice
Nov 17 19:47:32 Kubuntu kernel: [ 6145.356058] ppdev0: unregistered pardevice
Nov 17 19:47:34 Kubuntu kernel: [ 6147.312421] ppdev0: registered pardevice
Nov 17 19:47:34 Kubuntu kernel: [ 6147.360338] ppdev0: unregistered pardevice
Nov 17 19:47:35 Kubuntu kernel: [ 6147.401495] ppdev0: registered pardevice
Nov 17 19:47:35 Kubuntu kernel: [ 6147.448484] ppdev0: unregistered pardevice


---

### Post by linux23dragon on 2008-11-18
> **socngill said:**
> Here it is (it's quite long...)

The driver seems to be not working well.  I don't think its working for this kernel or udev and hal.


```
Nov 14 18:30:55 Kubuntu kernel: [ 17.084953] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 17.084961] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 17.085699] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.085702] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.085972] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 17.085975] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 17.086107] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.086110] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.086570] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 17.086573] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 17.086685] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 17.086688] ov51x_jpeg: Unknown symbol video_device_release
```

---

### Post by socngill on 2008-11-18
> **linux23dragon said:**
> The driver seems to be not working well.  I don't think its working for this kernel or udev and hal.


```
Nov 14 18:30:55 Kubuntu kernel: [ 17.084953] ov51x_jpeg: disagrees about version of symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 17.084961] ov51x_jpeg: Unknown symbol video_devdata
Nov 14 18:30:55 Kubuntu kernel: [ 17.085699] ov51x_jpeg: disagrees about version of symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.085702] ov51x_jpeg: Unknown symbol video_unregister_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.085972] ov51x_jpeg: disagrees about version of symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 17.085975] ov51x_jpeg: Unknown symbol video_device_alloc
Nov 14 18:30:55 Kubuntu kernel: [ 17.086107] ov51x_jpeg: disagrees about version of symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.086110] ov51x_jpeg: Unknown symbol video_register_device
Nov 14 18:30:55 Kubuntu kernel: [ 17.086570] ov51x_jpeg: disagrees about version of symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 17.086573] ov51x_jpeg: Unknown symbol video_usercopy
Nov 14 18:30:55 Kubuntu kernel: [ 17.086685] ov51x_jpeg: disagrees about version of symbol video_device_release
Nov 14 18:30:55 Kubuntu kernel: [ 17.086688] ov51x_jpeg: Unknown symbol video_device_release
```

That doesn't sound good!!  i might try live CDing 8.04 and 8.10 ( I did a direct upgrade so yu never onw, it might make a difference) and see if I get any positive results.

I really like my Kubuntu, but if you think another distro of Linux might provide better results let me know and I shall try a few Live CD's.

Thanks for your continued help - it's much appreciated :)

---

### Post by socngill on 2008-11-24
> **linux23dragon said:**
> The driver seems to be not working well.  I don't think its working for this kernel or udev and hal.

Since my last post i have had some limited success.  I found a thread which had an updated driver for the OV51 (or at least I think it was an updated version) and ther machine does at least seem to recognise that a video device is plugged in.  in the dev folder it is bringing up a video0 which it never did before, plus when plugged in the blue light on the cam comes on (it only ever did this before when I booted into XP).  However, I still can't get the programes to recognise it.  I have tried Skype, Cheese and VLC but none of them work - Skpye and Cheese say there is no cam, while VLC plays but nothing appears.

Since my last post I performed a clean install of Kubuntu 8.10, installed the backports and then installed this driver (having failed with the one in the repositories.  Any ideas as to what I could try next?

This is the thread with the link - on the bottom of the last page - [http://ubuntuforums.org/showthread.php?t=690666](http://ubuntuforums.org/showthread.php?t=690666)  I don't know if it will be of any help or not :)

---

### Post by socngill on 2008-11-30
dmsg brings up the following errors:

> [   14.845089] Linux video capture interface: v2.00                             
[   14.916398] ov51x_jpeg: USB OV519 video device found                         
[   15.282065] ov51x_jpeg: Unknown image sensor version: 2                      
[   15.282072] ov51x_jpeg: Failed to configure OV7xx0                           
[   15.282075] ov51x_jpeg: OV519 Config failed                                  
[   15.282080] ov51x_jpeg: Camera initialization failed                         
[   15.282101] ov51x: probe of 2-1:1.0 failed with error -5                     
[   15.282180] usbcore: registered new interface driver ov51x                   
[   15.282250] ov51x_jpeg: 1.5.9 : ov51x USB Camera Driver  

Any ideas what the error messages might mean, and how I might be able to fix them?

---

### Post by mocha on 2008-12-08
Can you try these instructions and let me know if it works:

[http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929]("http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929")

---

### Post by socngill on 2008-12-12
> **mocha said:**
> Can you try these instructions and let me know if it works:

[http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929]("http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929")

Hi Mocha.

I followed those instructions, and while it threw up no error messages, the cam still doesn't work.  video0 is present in dev folder, but nothing seems to want to play it.  I ran camstream but just got a greyish screen.  I also ran caminfo and got the following:

> neil@Kubuntu:~$ caminfo
CVideoCollector::VideoCollector()
>> CVideoDevice::CVideoDevice()
<< CVideoDevice::CVideoDevice()
>> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video0)
<< CVideoDeviceLinux::CVideoDeviceLinux()
>> CVideoDeivceLinux::~CVideoDeviceLinux()
<< CVideoDeivceLinux::~CVideoDeviceLinux()
>> CVideoDevice::~CVideoDevice()
<< CVideoDevice::~CVideoDevice()


So it knows that the cam is there.  It just doesn't seem to want to work.

Edit:  Also when I ran the camstream through the terminal I got this:

> neil@Kubuntu:~$ camstream
W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
<< void CCamStreamApp::ReadConfigFile()
>> virtual void CCamStreamMainWindow::closeEvent(QCloseEvent*)
  >> void CCamStreamMainWindow::CloseAll()
  << void CCamStreamMainWindow::CloseAll()
<< virtual void CCamStreamMainWindow::closeEvent(QCloseEvent*)
>> virtual CCamStreamMainWindow::~CCamStreamMainWindow()
  >> void CCamStreamMainWindow::CloseAll()
  << void CCamStreamMainWindow::CloseAll()
<< virtual CCamStreamMainWindow::~CCamStreamMainWindow()
>> void CCamStreamApp::SaveConfigFile()
<< void CCamStreamApp::SaveConfigFile()

---

### Post by mocha on 2008-12-25
Look at my post here

[http://ubuntuforums.org/showthread.php?t=1008404&highlight=vf0350]("http://ubuntuforums.org/showthread.php?t=1008404&highlight=vf0350")

I use this cam with Skype no problem.  Camstream shows its output fine.

---

### Post by socngill on 2009-01-10
> **mocha said:**
> Look at my post here

[http://ubuntuforums.org/showthread.php?t=1008404&highlight=vf0350]("http://ubuntuforums.org/showthread.php?t=1008404&highlight=vf0350")

I use this cam with Skype no problem.  Camstream shows its output fine.

Unfortunetly that hasn't helped either.  I think I might just give up until the next clean install of Kubuntu and then try it again.

Thanks for your help.

---

### Post by mocha on 2009-01-12
Maybe you have some old modules loading?  Without loading the hacked driver on your own, what does the output of "lsmod | grep -i ov" produce on your system?  There really should be no reason that the camera doesn't work for you.  There must be something simple we're missing here.

---

### Post by socngill on 2009-02-19
The command lsmod | grep -i ov gives the following output:

ov51x_jpeg            159224  0
videodev               41344  1 ov51x_jpeg
usbcore               149360  7 snd_usb_audio,snd_usb_lib,ov51x_jpeg,usblp,ehci_hcd,uhci_hcd

That's with everything loading on start-up as usual.  Strange as it seems to accept that the item is there and that the drivers are installed.

It probably is something very minor - like an old module or something which is conflicting with it.  Not done a clean install yet either.

---

### Post by Wiley_Linux on 2009-02-21
Try to check if you have permission to capture video from your Webcam in System->Administration->Users and Groups

I had the same problem, Camstream and skype didn't detect my webcam. I tried to uninstall and install the driver a lot of time and nothing. Finally, I changed my permission and everything worked.

good luck!

---

### Post by socngill on 2009-02-22
> **Wiley_Linux said:**
> Try to check if you have permission to capture video from your Webcam in System->Administration->Users and Groups

I had the same problem, Camstream and skype didn't detect my webcam. I tried to uninstall and install the driver a lot of time and nothing. Finally, I changed my permission and everything worked.

good luck!

I think I have managed to access this through "kuser", but what do I do know?  I can't see anything which says webcam?

---

### Post by socngill on 2009-02-22
OK.  I have gone into KUSER as root and added everything to my group.  Now Skype recognises that I have webcam but won't give a test piture.  howere when I tried a test call the wife said she could see me but that the picture was all wierd and the colour was not right.  Camorama connects but provides three of me in black and white while Cheese still doesn't recognise the cam.

Here are my current settings (for want of a better word)

MODULES:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ov51x_jpeg

MODPROBE.B OPTIONS

> # Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1

options ov51x_jpeg forceblock=1

and lsmod | grep ov brings up:

> ov51x_jpeg            159224  0
videodev               41344  1 ov51x_jpeg
usbcore               149360  7 snd_usb_audio,snd_usb_lib,ov51x_jpeg,usblp,ehci_hcd,uhci_hcd



Am i missing anything????

---

### Post by socngill on 2009-03-12
Bump.

---

