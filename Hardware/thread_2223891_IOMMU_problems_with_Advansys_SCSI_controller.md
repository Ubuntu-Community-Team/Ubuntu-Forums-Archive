---
title: "IOMMU problems with Advansys SCSI controller"
date: 2014-05-13
forum: Hardware
---

### Post by Gridwalker on 2014-05-13
Hi there,

I recently bought a chromecast and decided that I wanted to build myself an Ubuntu based media server for DLNA/uPnP streaming, but I'm very low on cash and had to build it out of scavanged spare parts. I have managed to obtain a Phenom 9550, an MSI MS-7508 motherboard and 4 gigs of RAM, but I was very short on storage space (a pair of 80gb IDE drives that I use for my OS and separately mounted home folder, plus an external 320gb USB drive that I use for storage) so I thought I would dust off an old Sun Microsystems SCSI storage box and bring it out of retirement as a 4 disk RAID 0 setup using an old Advansys ABP-930/40U SCSI adapter card. 

I am running Ubuntu 14.04 (AMD_64) and Plex media server.

When it runs, the system does its job perfectly; it streams HD movies to my chromecast with great quality and virtually no lag. The problem comes when copying media to or from the RAID, when the system freezes with memory addressing problems (frequently setting my file system to read only until I reboot). The problem wasn't too bad when I was initially running 2 gigs of RAM (just the occasional SIGSEV), but that RAM was very old and slowly degrading so I swapped it out for a 4gb stick (which testing shows is flawless) and the problems got much worse.

Now, when copying from the RAID to my USB disk, I can usually copy between 1 & 2 gigs before the process freezes with no visible error message in nautilus. Running "dmesg|tail" in the terminal brings up the following error repeated 10 times :
[INDENT]*ehci-pci 0000:00:04.1: PCI-DMA: Out of IOMMU space for 65536 bytes*[/INDENT]
The system then becomes unstable and I have to perform a hard reset.

The problems are worse when I am copying files from the USB disk to the RAID. I can usually copy around 500mb before I get an error message reporting "Error splicing file: Input/Output error". The system normally freezes at this point, and the file system is sometimes set to read-only until it has been reset and gone through the usual boot-up disk checks.

Sometimes I can run dmesg|tail at this point, and I think the relevant lines from that would be;
[INDENT][I]end_request: I/O error, dev sda, sector 51326816
atal: EH complete
usb 2-1: device descriptor read/64, error -11[/I][/INDENT]

Sometimes pressing ctrl+alt+f1 at this point brings up a screen full of PCI-DMA errors that scroll by so quickly that they are impossible to read.

Although I had similar problems before I upgraded my RAM, they were nowhere near as bad as they are now. I understand that that IOMMU is designed for managing memory assigned to older devices that can't handle 64 bit addressing, so it seems likely that the Advansys adapter is at fault here (POST information shows that the chipset dates back to 1998). I am also aware that IMMO has something to do with managing memory assigned to the AGP system, and I have an unused AGP slot on the motherboard. However, I am not sure if the AGP information is relevant, as I am currently using the onboard GeForce 8200 graphics card (which caused a whole host of driver problems on its own). 

I have checked through all of the motherboard settings for anything relating to IOMMU but can't find a single reference. 

I have seen a few suggestions whilst browsing forums that indicate placing an IOMMU parameter to the kernel configuration may solve the issue, however I am not certain that I am doing the right thing. To experiment with these kernel parameters, I have edited the boot options from the GRUB menu and temporarily inserted the suggested parameters to see if they make any difference.

So far, I have tried;
[LIST]
[*]IOMMU=MEMAPER=3
[*]IOMMU=SOFT
[*]IOMMU=FORCE
[/LIST]
Unfortunately, none of those have made much of a difference (besides marginally changing the byte value in the error message when copying from RAID to USB).

A friend has advised me that there is an old Advansys module that has not yet been deprecated, which I tried to run by adding "advansys" (without quotation marks) to the end of /etc/modules, however that had limited effect. The only difference this made was a reduced byte value in the IOMMU error message, similar to what happened when I tried IOMMU=SOFT in the boot options.

Although I should have a terabyte SATA drive on its way to me soon, I would still like to be able to use the RAID for something (I was thinking about using it to store torrent seeds, or something along those lines). Although I know my way around a few linux commands, I am not knowledgeable enough to pin down or solve the problem. Any help would be appreciated, but PLEASE be patient with me as there are some big gaps in my knowledge.

If I can stream 1080p movies from the RAID box, I know it HAS to be good for something!

---

### Post by matt_symes on 2014-05-13
Hi

Have you tried these ?

```
iommu=allowdac
```

You can also increase the window

```
memaper=2
```

Take a look in

```
Documentation/x86/x86_64/boot-options.txt
```

from the Linux sources.

So maybe try something like this as a kernel boot parameter.

```
iommu=allowdac,merge,memaper=2
```

EDIT:

What does this return ?

```
dmesg | grep "PCI-DMA:"
```

..as from the documentation in the sources

```
Currently four x86-64 PCI-DMA mapping implementations exist:

   1. <arch/x86_64/kernel/pci-nommu.c>: use no hardware/software IOMMU at all
      (e.g. because you have < 3 GB memory).
      Kernel boot message: "PCI-DMA: Disabling IOMMU"

   2. <arch/x86/kernel/amd_gart_64.c>: AMD GART based hardware IOMMU.
      Kernel boot message: "PCI-DMA: using GART IOMMU"

   3. <arch/x86_64/kernel/pci-swiotlb.c> : Software IOMMU implementation. Used
      e.g. if there is no hardware IOMMU in the system and it is need because
      you have >3GB memory or told the kernel to us it (iommu=soft))
      Kernel boot message: "PCI-DMA: Using software bounce buffering
      for IO (SWIOTLB)"

   4. <arch/x86_64/pci-calgary.c> : IBM Calgary hardware IOMMU. Used in IBM
      pSeries and xSeries servers. This hardware IOMMU supports DMA address
      mapping with memory protection, etc.
      Kernel boot message: "PCI-DMA: Using Calgary IOMMU"
```

Kind regards

---

### Post by Gridwalker on 2014-05-13
Thanks for the information! I have to go out shortly, so I can't try everything now, but here is the output of dmesg | grep "PCI-DMA:" :

[    0.832968] PCI-DMA: Disabling AGP.
[    0.833068] PCI-DMA: aperture base @ b8000000 size 65536 KB
[    0.833070] PCI-DMA: using GART IOMMU.
[    0.833074] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture

I will just try out a quick reboot with iommu=allowdac,merge,memaper=2 as a parameter and I will let you know if it helps :)

---

### Post by matt_symes on 2014-05-13
Hi

> PCI-DMA: using GART IOMMU

I believe those commands will work for you. 

```

  iommu options only relevant to the AMD GART hardware IOMMU:
    <size>             Set the size of the remapping area in bytes.
    allowed            Overwrite iommu off workarounds for specific chipsets.
    fullflush          Flush IOMMU on each allocation (default).
    nofullflush        Don't use IOMMU fullflush.
    leak               Turn on simple iommu leak tracing (only when
                       CONFIG_IOMMU_LEAK is on). Default number of leak pages
                       is 20.
    memaper[=<order>]  Allocate an own aperture over RAM with size 32MB<<order.
                       (default: order=1, i.e. 64MB)
    merge              Do scatter-gather (SG) merging. Implies "force"
                       (experimental).
    nomerge            Don't do scatter-gather (SG) merging.
    noaperture         Ask the IOMMU not to touch the aperture for AGP.
    forcesac           Force single-address cycle (SAC) mode for masks <40bits
                       (experimental).
    noagp              Don't initialize the AGP driver and use full aperture.
    allowdac           Allow double-address cycle (DAC) mode, i.e. DMA >4GB.
                       DAC is used with 32-bit PCI to push a 64-bit address in
                       two cycles. When off all DMA over >4GB is forced through
                       an IOMMU or software bounce buffering.
    nodac              Forbid DAC mode, i.e. DMA >4GB.
    panic              Always panic when IOMMU overflows.
    calgary            Use the Calgary IOMMU if it is available
```

Whether they will make a difference is another matter but it gives us a reference point to start working from.

I have to log off soon myself and i will not be back on until tomorrow so we can continue then.

Kind regards

---

### Post by Gridwalker on 2014-05-13
Ok, I have rebooted using the suggested IOMMU parameter and tried copying files from the RAID to my USB drive and we had a slightly different result. I managed to copy slightly more data before it froze, and I got a warning message from Nautilus this time (error splicing file: input/output error).

The result of dmesg|tail :
[  554.764953] advansys 0000:01:08.0: PCI-DMA: Out of IOMMU space for 57344 bytes
[  554.772943] advansys 0000:01:08.0: PCI-DMA: Out of IOMMU space for 57344 bytes
[  554.780940] advansys 0000:01:08.0: PCI-DMA: Out of IOMMU space for 57344 bytes
[  554.788927] advansys 0000:01:08.0: PCI-DMA: Out of IOMMU space for 57344 bytes
[  554.788944] sd 2:0:1:0: [sdc] Unhandled error code
[  554.788946] sd 2:0:1:0: [sdc]  
[  554.788949] Result: hostbyte=DID_SOFT_ERROR driverbyte=DRIVER_OK
[  554.788951] sd 2:0:1:0: [sdc] CDB: 
[  554.788952] Read(10): 28 00 00 53 70 a0 00 00 70 00
[  554.788961] end_request: I/O error, dev sdc, sector 5468320

dmesg|grep "PCI-DMA:" returns repeated variants of :
[  554.740397] ehci-pci 0000:00:04.1: PCI-DMA: Out of IOMMU space for 57344 bytes
and
[  554.788927] advansys 0000:01:08.0: PCI-DMA: Out of IOMMU space for 57344 bytes
and
[  632.883745] pata_amd 0000:00:06.0: PCI-DMA: Out of IOMMU space for 61440 bytes

---

### Post by matt_symes on 2014-05-13
Hi

BTW: Is you Ubuntu installation 64 or 32 bit ?

What does ```
uname -m
``` and ```
grep " lm " /proc/cpuinfo
``` return ?

Kind regards

---

### Post by Gridwalker on 2014-05-13
My installation is 64 bit, as I was planning to slowly increase the ram for better transcoding performance.

uname -m returns x86_64

grep " lm " /proc/cpuinfo returns the same result 4 times :
*flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock*

Thanks again for the help :)

---

### Post by Gridwalker on 2014-05-16
Ok, I haven't really had much time lately (end of uni semester) and I don't really want to have to input various permutations of IOMMU parameters and eliminate them by trial and error, so I'd like to know if there is a way of determining the optimum IOMMU configuration from the terminal?

At the moment, I don't really understand enough to do anything other than take random stabs in the dark.

---

### Post by matt_symes on 2014-05-16
Hi

I been pretty busy myself over the last couple of days an this is just a quick reply today.

I am not sure what is causing the overflow even after taking a quick look at amd_gart.c.

It's interesting that iommu=soft had no effect for you. That should have use the software iommu from what i can see.

It may be worth posting your entire dmesg output from boot up, to copying data to the drive and seeing if that holds some clues.

If you do that then post it to pastebin and post the link back here.

```
sudo apt-get install pastebinit
```

```
dmesg | pastebinit
```

Kind regards

---

### Post by Gridwalker on 2014-05-16
Heya,

No wories about not continuing this sooner, I'm sure we're both busy people :)

Since we last spoke, I have received a few new parts, so my system has undergone a bit of a tweak. Just so you know, I have my OS on one IDE drive, my home folder mounted on a second IDE drive, a sata drive for storage, my USB external and the RAID box. I don't know if the change is relevant, but knowing this might help when reading the logs.

After you said that you were surprised that using the "soft" option didn't work, I rebooted and tried "*IOMMU=soft,allowdac,merge,memaper=2*" as a set of parameters. After booting with that configuration I tried copying a 1gb file to the raid and it successfully copied the data across but then stopped reading the RAID. At first nautilus could see the array but wouldn't show any contents, then nautilus stopped working altogether. Unfortunately, I failed to get any output from dmesg on that occasion, but the following message was displayed in an infinite loop when restarting the system :
[INDENT]*ECHI-PCI 0000:00:04.1 : PCI-DMA out of IOMMU space for 4096 bytes*[/INDENT]

Still, copying across a 1gb file **to** the RAID is the best result that I've had so far!

Following your instructions, I have installed pastebinit and uploaded the dmseg output for a full boot>copy>crash cycle. On this test, I booted using the parameters listed above, then attempted to copy approx 4gb from the RAID to my new SATA drive.

[http://paste.ubuntu.com/7472728/](http://paste.ubuntu.com/7472728/)

I hope this helps.

---

### Post by Gridwalker on 2014-05-18
Quick update : I noticed SVM was enabled on my motherboard, so I disabled this to see if virtualisation support was mucking around with my IOMMU systems. No real change; I managed to copy slightly more data from the RAID to my USB drive (using the soft, allowdac, merge and memaper=2 parameters) but then it crashed with the usual error messages.

---

### Post by Gridwalker on 2014-05-18
EUREKA!!!

Sorry ... I got carried away.

I have solved the issue : your first suggestion was the correct one, but for some bizarre reason it was the order of the kernel parameters that was messing things up. I moved the iommu parameter from being the last on the list over to being the first on the list and it suddenly worked.

I have switched my adapter to UltraSCSI to double the speed and I am now 28Gb into a 215Gb transfer without any problems at all :)

Thanks for the help :)

---

### Post by matt_symes on 2014-05-19
Hi 

Excellent ! I'm glad it's fixed.

I was planning on continuing this thread this evening, after the beautiful weather over the weekend in the UK when i hardly touched a computer, but it looks like you've fixed it :).

Kind regards

---

