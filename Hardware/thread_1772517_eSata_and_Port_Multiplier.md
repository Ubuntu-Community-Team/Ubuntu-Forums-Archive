---
title: "eSata and Port Multiplier"
date: 2011-05-31
forum: Hardware
---

### Post by TCT on 2011-05-31
I am trying to get an eSATA PCI-E card working under Linux with a multi-drive enclosure that uses Port Multiplier.

I have tried four different eSata cards, two from Addonics, a cheap Chinese no-name card, and a CardBus card in a laptop. One PCI-E, one PCI-X, one PCI, and one CardBus.
I have tried several different eSATA enclosures, one from BYTE-CC, one from Thermaltake, and a cheap Chinese no-name brand.
I have tried in a Dell Optiplex 745, a Dell Precision T3400, am HP Z200 Workstation, and a Dell Inspiron 8600 laptop using an eSATA CardBus card.

The eSATA hba cards were using either Silicon Image 3124 or Sillicon Image 3132 chips. I cannot tell what Port Multiplier chips were in the enclosures.

*ALL* of these combinations work under Windows XP and Windows 7.
*NONE* of these combinations work under Ubuntu, or any of 5 or 6 different distros I have tried.

The best I could get is 'fdisk -l' shows the first drive, but not the second.

I have searched all over Google and the web for information on this, but the information is terribly out of date. Can someone PLEASE just tell me the exact brand name of a PCI-e eSATA card that is KNOWN PERSONALLY to have Port Multiplier to work under Ubuntu. Don't believe what the manufacturer says on NewEgg.

---

### Post by TCT on 2011-05-31
I don't know if this will help anyone, but here are the messages from 'dmesg' when I plug a hard drive into an eSATA port:

[ 1433.569951] ata2: irq_stat 0x00b40090, PHY RDY changed
[ 1433.569960]  ata2: limiting SATA link speed to 1.5 Gbps
[ 1433.569965] ata2: hard  resetting link
[ 1435.766260] ata2: SATA link up 1.5 Gbps (SStatus 113  SControl 10)
[ 1435.767097] ata2.15: Port Multiplier 1.1, 0x197b:0x2352 r0, 2  ports, feat 0x0/0x0
[ 1435.767102] ata2.15: Asynchronous notification not  supported, hotplug won't
[ 1435.767104]          work on fan-out ports. Use  warm-plug instead.
[ 1435.767295] ata2.00: hard resetting link
[  1436.102601] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  1436.102667] ata2.01: hard resetting link
[ 1436.438741] ata2.01: SATA link  up 1.5 Gbps (SStatus 113 SControl 310)
[ 1441.436783] ata2.00: qc timeout  (cmd 0xec)
[ 1441.436812] ata2.00: failed to IDENTIFY (I/O error,  err_mask=0x5)
[ 1441.436818] ata2.15: hard resetting link
[ 1443.636201]  ata2.15: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 1443.637048]  ata2.00: hard resetting link
[ 1443.972786] ata2.00: SATA link up 1.5 Gbps  (SStatus 113 SControl 310)
[ 1443.972878] ata2.01: hard resetting link
[  1444.308694] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  1454.305398] ata2.00: qc timeout (cmd 0xec)
[ 1454.305427] ata2.00: failed to  IDENTIFY (I/O error, err_mask=0x5)
[ 1454.305433] ata2.15: hard resetting  link
[ 1456.504901] ata2.15: SATA link up 1.5 Gbps (SStatus 113 SControl  10)
[ 1456.505731] ata2.00: hard resetting link
[ 1456.841409] ata2.00:  SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1456.841554] ata2.01: hard  resetting link
[ 1457.177347] ata2.01: SATA link up 1.5 Gbps (SStatus 113  SControl 310)
[ 1487.168844] ata2.00: qc timeout (cmd 0xec)
[ 1487.168874]  ata2.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 1487.168880] ata2.00:  failed to recover link after 3 tries, disabling
[ 1487.168886] ata2.15: hard  resetting link
[ 1489.368282] ata2.15: SATA link up 1.5 Gbps (SStatus 113  SControl 10)
[ 1489.688703] ata2.01: hard resetting link
[ 1490.088812]  ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1495.086786]  ata2.01: qc timeout (cmd 0xec)
[ 1495.086817] ata2.01: failed to IDENTIFY  (I/O error, err_mask=0x5)
[ 1495.086824] ata2.15: hard resetting link
[  1497.286222] ata2.15: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[  1497.606644] ata2.01: hard resetting link
[ 1497.942829] ata2.01: SATA link  up 1.5 Gbps (SStatus 113 SControl 310)

---

### Post by TCT on 2011-05-31
OK, I've been working on this on and off for months. I found this: [http://patchwork.ozlabs.org/patch/90211/](http://patchwork.ozlabs.org/patch/90211/) a patch someone made to add some quirk handling in the libata driver specifically for whatever port multiplier chip is buried inside the ThermalTake BlackX Duet hard drive docking station.

I crossed my fingers and hoped the patch made it into Ubuntu 11.04. I got my hands on a ThermalTake BlackX Duet and it worked!!!!

So, for the record, here is a combo that works:

Running Ubuntu 11.04 on an HP Z200 workstation with an Addonics ADSA3GPX1-2E 2 port eSata PCI-e hba. Plugging 2 hard drives into a ThermalTake BlackX Duet hard drive docking station. fdisk -l shows BOTH hard drives are visible. Hot-swapping doesn't seem to work, but you can power off the dock and swap drives.

I suspect any Sil3132 based hba will work (2 port PCI-e eSATA).
There is no way to tell which Port Multiplier chip is inside each enclosure or docking station, so stick with the ThermalTake BlackX Duet.

Now... anyone want to tell me how to find out if the port multiplier is using Command Queuing or FIS queuing? :-)

---

### Post by zephyr707 on 2011-06-09
Hi TCT,

I have a Rosewill RSV-S8.   In the manual it says that the port-multiplier design is based on the silicon image Sil3726 if that helps any.  I am currently trying to get it working with my laptop (have posted a thread [here]("http://ubuntuforums.org/showthread.php?p=10922454#post10922454")), but I'm not sure if it is possible with my intel chipset.  Too bad it is not as simple as plugging it in!

wonder if that thermaltake will work for my setup, hehe

---

