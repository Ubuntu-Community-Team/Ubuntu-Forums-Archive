---
title: "SATA configuration"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by marcadams on 2005-04-01
Hi ;

I have a DIAMONDMAX SATA 80GB HD. 

I would like to know if it is optimally configured. For example to make sure DMA is switched on.

I have found other threads mention the following command:
"
for disc in `ls /dev/hd?`; do hdparm $disc; done
"

However, the only device it finds is HDC - which I think is a CDROM.

Could someone, please let me know where the SATA hard drive device is kept, so I can  use the above command to see if DMA is turned on.


Many thanks
Marc

---

### Post by Dracontopes on 2005-04-01
My SATA drives are located on /dev/sda and /dev/sdb ...

---

### Post by alastair on 2005-04-01
If you want to understand what hardware is seen, and drivers loaded (etc.), it is a good habit to get into to look through the boot/syslog messages - written as the kernel loads and various things are probed and loaded i.e. check out :

/var/log/syslog

You should see reference to disk channels and disks found e.g. I see things like :

```
ICH4: chipset revision 1
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: ST9100823A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3

```

For SATA, this uses the SCSI layer, so you will see devices like /dev/sda (not /dev/hda like I have).

---

### Post by marcadams on 2005-04-02
Thanks for your help;

By running:

for disc in `ls /dev/sd?`; do hdparm $disc; done

I get:


/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9964/255/63, sectors = 81964302336, start = 0

Can this be tweaked for performance, or should it just be left alone?
E.g. I notice it is set to 16-bit, could it be set to use 32 bit?

Many thanks
Marc

---

### Post by maqi on 2005-04-02
Try 'man hdparm' or 'hdparm --help'. There's lots you can tweak if your drive supports it.

Also - easy way to get your boot log: 

$ dmesg > ~/Desktop/bootlog

This creates a text file containing all boot messages on your desktop. No sudoing and no digging around the file system :)

---

### Post by darkaudit on 2005-04-08
I just put together a new system, with a SATA drive as it's sole hard drive. When I try to change any hdparm settings, I get 'operation not permitted'. The DVD burner was from another system that had just IDE drives, and I was able to set DMA and such.

My first idea is to put in an IDE drive as the primary drive. Is there another option?

Board is an Abit NF7-S v.2 with a Silicon Image onboard SATA controller.

---

### Post by maqi on 2005-04-13
I have 2 SATA drives only on my system. Everything works fine. Doesn't seem subjectively slower than SATA in Windows - but I haven't done the benchmarks. And going by the SATA specs these drives should be faster than they are in Linux - at least if you do the hdparm tests.

But hdparm only works for IDE devices. Linux deals with SATA as a SCSI device so hdparm doesn't alter the settings.

I haven't had much luck googling to find some similar configuration app for SCSI/SATA devices. Plenty of ppl looking for one though ;)

maqi

---

