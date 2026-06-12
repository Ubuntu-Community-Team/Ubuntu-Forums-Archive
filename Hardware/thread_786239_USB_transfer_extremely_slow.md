---
title: "USB transfer extremely slow"
date: 2008-05-07
forum: Hardware
---

### Post by Victormd on 2008-05-07
I don't know if this is a coincidence or a bug or something I messed up, but my USB transfers have become erroneous and extremely slow.
Today I downloaded ~250MB worth of photos from my digital camera. Not only did it take forever, but about 10% of the photos copied had errors (color mismatch/cropped photos - the photos on the camera were fine). I thought it might be just the camera but now I'm backing up some files for work on a flash drive (~180MB) and it's been copying for 20 min and 7 min still to go...
Has this happened to anyone else? Any suggestions???

---

### Post by Victormd on 2008-05-08
Bump

---

### Post by michaelaly on 2008-05-08
I'm having USB issues as well since installing Hardy Heron. A number of times the file manager has crashed while copying files to an external hard drive, and the transfer speed is painfully slow. Any suggestions?
thanks

---

### Post by crash91 on 2008-05-22
I can confirm this. It may be a bug..the larger the file the more the speed decreases.

---

### Post by Jimmy The Chip on 2008-05-25
Me too. 

I don't suppose any of you have been using USB with VirtualBox? 

Has anyone got this with a pure fresh install of hardy?

---

### Post by Juan_VCS on 2008-05-26
Same here.

---

### Post by krisvdm on 2008-10-11
Im having the same problem.  Previously on Ubuntu (Edge 32 bit version), my USB ports worked fine (fast).
Now having Ubuntu 8.04 (Hardy 64 bit version), the USB is painfully slow.

---

### Post by Thanh-BKK on 2008-10-14
Hi :)

Exactly same problem here, forum threads(s) never got replied to. Transferring 4 GB of data from HDD to thumb drive takes 45 minutes, in Windows it takes 6 minutes. READING is fast under Ubuntu. 

Best regards.....

Thanh

---

### Post by bastek72pl on 2008-10-19
Same issue here. Windows (same laptop) does it 10 times faster.

---

### Post by slumbergod on 2008-10-30
Both Gutsy and Hardy have been pathetic for file transfer speeds using my flash drive. I thought it might have been my aging laptop but a few months ago I bought a new laptop and the problem persists. 

I have friends running Hardy on their laptop and transfer speeds seem normal for them. If I boot into Windows XP the transfers are as fast as they should be.

This is one of the few things I find frustrating about Linux. I am sure there is a reason and a solution somewhere but I have yet to find it. No one seems to know why...you're either lucky or unlucky on this one.

---

### Post by BrownieMan on 2008-12-02
I'm finding this problem throughout the board for Hardy. A common threat seems to be a lack of DMA working on the drives.

I came across [this link]("http://linux-ata.org/faq.html") that might have some help. I haven't tried the suggestions yet. But I should have results within the hour.

I'm specifically looking at this part

```
Intel combined mode

Why does my IDE hard drive run at 3MB/s, while SATA runs at full speed?
Why does my IDE drive or CD-ROM not use DMA, while SATA works just fine?

This is an unfortunate side-effect of two things: "combined mode" &#8212; a particular configuration of Intel motherboard devices, where PATA and SATA are combined into a single PCI function &#8212; and the state of libata, which at the time of the design decision had stable ATA disk support, but not ATAPI device support.

The net result is that two drivers, the drivers/ide IDE driver and libata, are both trying to drive [different parts of] the same piece of hardware. That's possible, but only if one (and only one) driver does DMA.

This default configuration must stay in place these days only for backwards compatibility, and may be overridden in a multitude of ways:

    * Recommended (where BIOS permits): Change BIOS IDE mode from "legacy" or "combined" mode to "AHCI" (recommended), "RAID" or "native".
    * Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.
    * Disable libata (CONFIG_ATA) entirely, and enable CONFIG_BLK_DEV_IDE_SATA.
    * (newer choice, with less field testing) Disable CONFIG_IDE, and permit libata to run all your IDE and SATA ports.

```


I just tried fiddling with my BIOS, no such luck there. I didn't even see the option for IDE mode, but did see some other things.

---

### Post by tardeevo on 2008-12-04
Bad USB2.0 issues here too with Kubuntu 8.04-64, and I'm not on a laptop but a desktop.
First there is a weird polling error messages flooding on system logs:
```
[  217.636897] sd 4:0:0:1: [sdc] READ CAPACITY failed
[  217.636899] sd 4:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  217.636902] sd 4:0:0:1: [sdc] Sense not available.
[  217.636921] sd 4:0:0:1: [sdc] Write Protect is off
[  217.636923] sd 4:0:0:1: [sdc] Mode Sense: 00 00 00 00
[  217.636924] sd 4:0:0:1: [sdc] Assuming drive cache: write through
[  218.377149] sd 4:0:0:1: [sdc] READ CAPACITY failed
<repeat the above forver>

```
Then I'm experiencing sudden disconnections or errors after mounts of external high-speed usb devices (hard drives interfaces, mmc-cards and so on). Dmesg shows these many times:
```

kernel	[  488.515855] usb 6-4: device not accepting address 8, error -110
kernel	[  488.557334] usb 6-4: new high speed USB device using ehci_hcd and address 9
kernel	[  492.420208] usb 6-4: device not accepting address 9, error -110
<etcetera>

```
Why I talk about USB 2.0 only?
Because if I remove the ehci module with ```
sudo rmmod ehci_hcd
``` then I got everything working but with USB1.0 speeds.

Then I tried with enabling "USB Legacy feature" from my BIOS but with no luck and at last tried [this ]("http://ubuntuforums.org/showthread.php?p=5447719#post5447719") but has failed has well.
I guess this is a really nasty boog to catch.

---

### Post by jamesnmandy on 2009-02-20
bad bug, really bad, i will be uninstalling Ubuntu unless this gets fixed soon, i use my external 750Gb HDD way too much for this crap, what takes minutes in windows now takes hours...

---

### Post by __ShaM__ on 2010-01-02
> **Victormd said:**
> I don't know if this is a coincidence or a bug or something I messed up, but my USB transfers have become erroneous and extremely slow.
Today I downloaded ~250MB worth of photos from my digital camera. Not only did it take forever, but about 10% of the photos copied had errors (color mismatch/cropped photos - the photos on the camera were fine). I thought it might be just the camera but now I'm backing up some files for work on a flash drive (~180MB) and it's been copying for 20 min and 7 min still to go...
Has this happened to anyone else? Any suggestions???
Do anyone experience very slow speed while transferring files to USB in ubuntu 9.10 , if so try to remount the USB device and fasten the copy process.

code:
sudo mount -o remount,async /media/mountpoint

before, my copying speed was 25 mins for a 700 MB file , after re mount using the above command it was less than 3 mins

EDIT: Me TOo NewBie In Ubuntu wOrld, So Dun AsK Me Any Problem If U Got :D, Thanks In Advance!

---

### Post by villain222 on 2011-03-15
extremely old, but the remount did work.  went from 300kb to 11mb, but its still very slow.  in theory the usb2.0 should be getting close to 50mb/s

---

