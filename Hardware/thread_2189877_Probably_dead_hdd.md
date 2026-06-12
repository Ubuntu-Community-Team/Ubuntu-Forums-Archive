---
title: "Probably dead hdd"
date: 2013-11-24
forum: Hardware
---

### Post by commander.sirowub on 2013-11-24
Hi there,

since today I'm unable to start up my laptop (Ubuntu 12 [Wubi], Windows 7). Windows does not give me any indication at all (continuesly loading hdd during loading-screen), while Ubuntu complains (after a bit of loading), that it is unable to find/load the boot-image.

So the first thing I tried was booting into Windows 7 DVD recovery console and running chkdsk c: /F /R (NTFS file system on disk), which found 4 defect sectors and marked them as defect.
This however didn't fix anything, as I was still unable to boot either into Ubuntu, nor Windows.

Next I tried booting into my Ubuntu ISO on my (backup) USB-Stick so that I atleast would be able to move some files to my external disk...
But my USB-Stick still failed to boot, because half-way through boot process it tries to access my hdd and continously fails with
```

[ ... ] ata1.00: exception Emask 0x0 SAct 0x1000000 SErr 0x0 action 0x0 
[ ... ] ata1.00: irq_stat 0x40000008 
[ ... ] ata1.00: failed command: READ FPDMA QUEUED 
[ ... ] ata1.00: status: { DRDY ERR } 
[ ... ] ata1.00: error: { UNC }

```

Is there any way to stop the USB-Boot image from accessing my hdd, while still later beeing able to recover data (mainly documents) from it? *sadface*

---

### Post by Kirboosy on 2013-11-25
Welcome to the forums! I would recommend you run some diagnostics on the hard drive. Most likelythe computer  includes some diagnotics built into the motherboard. Without the exact make and model it would be hard to say for sure.

If it doesn't have diagnostics then a handy tool that I use is [Ultimate Boot CD (UBCD)]("http://www.ultimatebootcd.com/") This CD will allow you to test all the hardware in the laptop.

Is your USB boot image a clean image of Ubuntu or is it a backup of your desktop? You may find better luck with a fresh image of Ubuntu and using the 'Startup Disk Creator' included in Ubuntu. 

Hope that helps!
~Caboose

---

### Post by commander.sirowub on 2013-11-26
Thanks you Cabosse(885) for your reply *happyface*

I'll first try out UBCD first, especially parted magic seems promising. :)

---

