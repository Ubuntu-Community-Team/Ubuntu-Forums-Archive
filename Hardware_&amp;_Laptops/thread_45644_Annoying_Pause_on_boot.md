---
title: "Annoying Pause on boot"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by sadza on 2005-07-01
Hey, my laptop using both the newest 686 and 386 kernels pauses for 20 secs at starting ubuntu... during boot. So I removed quiet from menu.lst and I found out the pause is actually at 
```
ide1 at 0x170-0x177,0x376 on irq 15
```
the lines before and after this are:
```
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3
Probing IDE interface ide1...
hdc: HL-DT-STDVD-ROM GDR8081N, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
ide4: Wait for ready failed before probe !
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (447 pages freed)
Restarting tasks... done
ext3: No journal on filesystem on hda3

```

I noticed this doesnt happen if I use the recovery mode. If anyone has any ideas on how to fix this or increase boot speed I would appreciate it. I did try remove network set up from boot but this caused my X login to take forever.

Thanks

---

### Post by sboetsch on 2005-10-05
Hello,

   I have the same problem.
   I test some other distribution and I got the same thing with Kubuntu 5.10 Preview (quite logical...), Fox Desktop and Elive (installed on hard disk).
   Only Mandriva does not have the problem (perhaps another distro I don't tested too).

   It is the only one problem I have with Ubuntu. All other things work nicely.

My hardware: Toshiba laptop Satellite 2410-S514 (p4 m, nvidia 420 go, ...).
My software: Ubuntu 5.04, Mandriva LE 2005, Windows XP.

If someone has a solution...
Thanks

---

### Post by pardasaniman on 2005-10-08
Ihave a toshiba 2400...

You can solve this by changing your kernel boot parameters.

You know you don't have disks on ide2-ide5 so add
ide2=noprobe ide3=noprobe ide4=noprobe ide5=noprobe

Should speed things up

I'm beta testing Breezy right now.. This problem has returned for me.. I can't figure out a work-around

---

