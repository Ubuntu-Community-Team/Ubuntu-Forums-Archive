---
title: "Card reader only works if inserted at boot time"
date: 2009-11-01
forum: Hardware
---

### Post by darkshadow on 2009-11-01
I just bought a new laptop "Acer Aspire 8940G-6683" but I am having a little trouble with the card reader.

If I have a SD card inserted when booting the laptop it works perfect. I can unmount take it out and put it back in and it mounts correctly like it should.

But if nothing is inserted when booting I am unable to make it work for any reason. it does not load the modules and even if I manually load the modules it does not start working.

I listed all the modules with lsmod when booting with a card in and then again without the card in and compared them to get the following list of modules that are loaded as a result of the card

fat
iee1394
jmb38x_ms
memstick
vfat
jmb38x_ms
memstick
mmc_block
nls_cp437
nls_iso8859_1
ohci1394
sdhci
sdhci_pci
vfat

What can I do to make this work without the card in at boot time since past loading those modules manually I don't know what to do. I am confused as to why loading them manually does not work.

---

### Post by darkshadow on 2009-11-01
I just noticed one thing that makes a difference. lspci has different output depending on if the card was inserted during boot time.

These lines are added when booting with the card in, but don't show if booted without the card in. This is a built in card reader.


0b:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0b:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
0b:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
0b:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0b:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

---

### Post by darkshadow on 2009-11-01
Once I found out the differences in lspci it did not take much time on Google to fix this problem.

I just had to add "pciehp.pciehp_force=1" into my Grub config file and everything started working.

---

