---
title: "All Sorts of Hardware Problems"
date: 2008-06-18
forum: Hardware
---

### Post by Imaginary on 2008-06-18
So I just installed a new motherboard (MSI K9N2G Neo), with an nVidia GeForce 8200 chipset.  Onboard video, onboard LAN, onboard sound (Realtek ALC888), onboard SATA.

I had a miserable time getting the nVidia binary drivers working on it, but that doesn't compare to the problems I've had with:

* LAN: doesn't manage to find the network.  Manually configuring the network interface can get me an IP6 address, but I never get an IP4, and can't see in or out from the machine.  Currently fixed with a PCI NIC.

* SATA: Hangs up while trying to boot from the SATA harddrive on the onboard controller.  Error messages similair to [http://ubuntuforums.org/showthread.php?t=776136](http://ubuntuforums.org/showthread.php?t=776136) along the lines of:

```
ata1 Sata link up 1.5 Gbps SStatus123 Scontrol300
[pause for a while]
ata1.00 qc time out (cmd 0xec)
ata1.00 failed to IDENTIFY (I/O error err_mask=0x4)
ata failed to recover some devices, retrying in 5 seconds
```

Which eventually gives up and boots into busybox with no ability to see the harddrive.  LiveCD is likewise unable to find the SATA hard drive.  Interestingly enough, the hard drive works well enough to get me to/through GRUB and to uncompress the kernel from, it just gives up midway through the start up.  Currently fixed with a PCI SATA controller.

* SOUND: Lots of static bursts.  LOTS of static bursts. I realize that the ALC888 isn't a symphonic grade chip, but I get less noise on my 15 years old cassette tape deck.  Currently fixed with a PCI SB Live.

Now, the interesting thing about all these problems, other than the fact that they're all my problem, is that lspci seems be having great difficulty recognizing the hardware for any of them.

```
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
```

and so on.  None of the functionality provided by the GeForce 8200, video services aside, seems to be getting recognized by lspci.

So, anyone have any thoughts?  Those related to my problem would be especially helpful.

---

### Post by Imaginary on 2008-06-18
*sad looking bump with puppy-dog eyes*

---

### Post by cdtech on 2008-06-18
Have you set your BIOS setting to both P-ATA & S-ATA mode?

---

### Post by markbuntu on 2008-06-19
It does sound like the bios is confused.

---

### Post by Imaginary on 2008-06-20
> **cdtech said:**
> Have you set your BIOS setting to both P-ATA & S-ATA mode?

Something is certainly badly confused.  I seem to recall checking both the IDE and AHCI modes in the BIOS with no luck, but I'll have to double check; I'm leaving town for the next few days and won't have a chance to poke at this problem until I get back.

I did however find another failing device, and some more information.  The USB EHCI mode devices seem to not recognize external USB 2 devices.  USB 1 OHCI devices come up fine, and if I rmmod ehci_hcd then the USB 2 devices can mount, but of course only at the lower speeds.

I've tried digging a bit more information about about what the system thinks about the hardware.  lspci -vv -n provides a little more information:

```
00:06.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0759] (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device [f462:7511]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

```

All of the other problematic devices are reporting the same way.  Unknown device, and access denied on the capabilities.

The other thing I stumbled across is that the SATA, the Ethernet, the USB ports, all of it, either shows up as "Green entries are new submissions not approved by the maintainers yet." on the pci.ids file at [http://pci-ids.ucw.cz/iii/?i=10de](http://pci-ids.ucw.cz/iii/?i=10de) or doesn't show up at all.

Does this mean I'm SOL on the 2.6.24 kernel?  And if so, is this the sort of thing that Ibex addresses?

---

