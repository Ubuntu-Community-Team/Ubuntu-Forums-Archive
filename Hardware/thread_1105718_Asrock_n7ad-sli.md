---
title: "Asrock n7ad-sli"
date: 2009-03-25
forum: Hardware
---

### Post by computx on 2009-03-25
My old mobo's sound and network has gotten flaky so I ordered a new Asrock n7ad-sli only to discover [phoronix]("http://www.phoronix.com/scan.php?page=article&item=asrock_n7ad_sli&num=1") lists this as currently incompatible with Ubuntu Linux including 8.10 and 9.04.
They assume the nforce 740i-sli chipset is to blame. My question is, does anyone else have any real world experience with this board? 
 Also is there work being done on nforce 740i drivers?
If I thought this would be supported in 6 months or so I might keep it as it has a good combination of features I wanted.

---

### Post by rmeu on 2009-07-24
Actually I made the same mistake as you. I needed to have a new PC as my previous one gave up. I found one based on the same motherboard  without looking over any possible incompatibility.

So well, for me I found out that - contrary to what the phoronix review says - I can run the LiveCD of Kubuntu 9.04 without problem. :P

However, After re-partitionning and installing, the boot up process fails with a message something like "Kernel panic - not syncing".

So maybe that problem is somewhere else. I need to test/check further...

---

### Post by computx on 2009-07-25
The asrock is still running fine with ubuntu for me. The phoronix review should be amended and i suggested they do so but last time I checked they hadn't.

---

### Post by chrisfu on 2009-08-28
I nearly had a heart attack when I read that review, as I've just today ordered that very same mobo with intentions of using my current Ubuntu install on the new rig I'm building.

I'll post back once it's built to let you know how it went. :)

---

### Post by chrisfu on 2009-09-03
> **chrisfu said:**
> I nearly had a heart attack when I read that review, as I've just today ordered that very same mobo with intentions of using my current Ubuntu install on the new rig I'm building.

I'll post back once it's built to let you know how it went. :)

Well, my old install works *almost* perfectly in the new rig.

The only problem seems to be that an older IDE DVD drive I use doesn't seem to be detected.  It's detected in the BIOS correctly, but doesn't show up in dmesg.

My device setup is as follows:

IDE-0.0: DVD *not detected with either with CS or MASTER jumpers set*
IDE-0.1: *empty*
SATA-0: Primary HDD
SATA-1: Secondary HDD
SATA-2: DVD-RW
SATA-3: *empty*
SATA-4: *empty*
SATA-5: *empty*

Anybody got any ideas why this wouldn't be working?  cdrecord --scanbus doesn't show the device up either.

Kind regards,

Chris

---

### Post by computx on 2009-09-03
Hmmm, I would suspect that you have a hardware problem. Are you sure its detecting it in the bios? If not it is probably a cable either the power or data unplugged. If you are sure the cables are plugged in and it is being picked up in the bios then I have more questions to ask. For instance does anything happen when you open the drive and insert a disc? Also what does the command ls -la /dev/cdrom return?

---

### Post by Steus83 on 2009-09-04
Hello All! :D

I'm new in this forum, but i use Ubuntu from several years... as chrisfu i bought this Asrock MOBO after that lighting destroy my old MOBO, and i've the same problem:
Old installation of Ubuntu JJ correct function, but DVD Drive not been recognize by OS (Bios recognize correctly):(. 

I had try different ways:

1. Switch AHCI / IDE
2. Re-install OS (but during boot of Live CD BusyBox appear and installation is stopped)
3. Use of different Live CD (Fedora or Suse) the problem is the same.


I suppose that the problem is IDE interface of Nforce. Therefore in the next days i try to buy sata dvd-rom and after i post my result on this thread. :)

Best Regards

Stefano

---

### Post by chrisfu on 2009-09-04
> **computx said:**
> Hmmm, I would suspect that you have a hardware problem. Are you sure its detecting it in the bios? If not it is probably a cable either the power or data unplugged. If you are sure the cables are plugged in and it is being picked up in the bios then I have more questions to ask. For instance does anything happen when you open the drive and insert a disc? Also what does the command ls -la /dev/cdrom return?

Well, the drive works in other machines perfectly fine.  It's definitely detecting it in the BIOS, and the power and IDE cables are in securely.  I can't do an ls on the device, as it doesn't exist.  It's absolutely positively not detected during boot, and doesn't show up anywhere in dmesg log.  It also isn't detected when using a Knoppix CD.

> **Steus83 said:**
> Hello All! :D

I'm new in this forum, but i use Ubuntu from several years... as chrisfu i bought this Asrock MOBO after that lighting destroy my old MOBO, and i've the same problem:
Old installation of Ubuntu JJ correct function, but DVD Drive not been recognize by OS (Bios recognize correctly):(. 

I had try different ways:

1. Switch AHCI / IDE
2. Re-install OS (but during boot of Live CD BusyBox appear and installation is stopped)
3. Use of different Live CD (Fedora or Suse) the problem is the same.


I suppose that the problem is IDE interface of Nforce. Therefore in the next days i try to buy sata dvd-rom and after i post my result on this thread. :)

Best Regards

Stefano

I agree with you on that one.  The nForce IDE driver in the current kernel probably doesn't support the newer nForce PATA interfaces properly, I'd imagine.  I have another IDE DVD drive (a DVD+/-RW DL burner) that I can try.  If that doesn't work either, then that will be the reason why.  By the way, have you tried flashing the BIOS to the latest version?  Mine came with P1.10 but I believe version P1.30 has come out now.  Perhaps that will work?

I'm sure the SATA DVD drive will work fine for you.  Mine works fine, but I'm still determined to get my old IDE DVD reader working.  There's no reason why it shouldn't!

---

### Post by chrisfu on 2009-09-04
>            *-ide **UNCLAIMED**
                description: IDE interface
                product: PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a0
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress cap_list
                configuration: latency=0

There we have it.  The PATA controller isn't yet supported.

---

### Post by computx on 2009-09-04
I am using a sata dvd-rw so I never tried the pata support. Sata drives are cheap now but it's a shame the pata support is broken.

---

### Post by chrisfu on 2009-09-29
Just to update everyone, this board uses the following chip for it's PATA functionality:

[http://www.via.com.tw/en/products/peripherals/1394/vt6330/](http://www.via.com.tw/en/products/peripherals/1394/vt6330/)

Edit below:

Ok, so I've done even more digging and found out a few things.  Firstly, this chip is a mash of two earlier released chips that are both supposed to be supported.  The firewire portion of the chip is supported, as should be the PATA parts.  The PATA functionality is based off the [VT6415]("http://www.via.com.tw/en/products/peripherals/pci_pcie/vt6415/") PATA controller.

After checking the pata_via module source, it's apparent that the VT6415 is indeed supported as of 2.6.28.  Also, it's also apparent that the VT6330's PATA functionality does indeed report itself to be the VT6415, as per below.  The bolded text is the vendor_id and the pci_id for the VT6415:

> 01:00.1 IDE interface [0101]: VIA Technologies, Inc. PATA IDE Host Controller [1106:0415] (rev a0) (prog-if 85 [Master SecO PriO])
	Subsystem: ASRock Incorporation Device [**1849:0415**]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at dc00 [size=8]
	Region 1: I/O ports at d480 [size=4]
	Region 2: I/O ports at d400 [size=8]
	Region 3: I/O ports at d080 [size=4]
	Region 4: I/O ports at d000 [size=16]
	Expansion ROM at f7fe0000 [disabled] [size=64K]
	Capabilities: <access denied>

So in short, this should work... but doesn't. :)  I'll have a scour around now to find out if anyone with the single (non combo) VT6415 controller is having issues too.  I've also made a post on the kernel mailing list.

---

### Post by chrisfu on 2009-10-20
I've been in correspondance with VIA regarding this issue, and they've now submitted a patch for inclusion into the kernel.  More details below:

[http://lkml.indiana.edu/hypermail/linux/kernel/0910.2/00036.html](http://lkml.indiana.edu/hypermail/linux/kernel/0910.2/00036.html)

Please let me know if it works for you.

---

### Post by chrisfu on 2009-11-29
The patch has been included in the next kernel, which should be hitting karmic-proposed in the next week or so. :)  If you can't wait, you can try a pre-release of the kernel (2.6.31-16pre2) at the following URL: [https://launchpad.net/~stefan-bader-canonical/+archive/karmic](https://launchpad.net/~stefan-bader-canonical/+archive/karmic)

---

