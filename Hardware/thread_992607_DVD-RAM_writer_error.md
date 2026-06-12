---
title: "DVD-RAM writer error"
date: 2008-11-24
forum: Hardware
---

### Post by tuskpc on 2008-11-24
I'm not sure what caused this problem.  After I upgraded to 8.10, via the internet, I have had problems with my DVD player.  I cannot even get it to detect the 8.10 live-cd I burned afterward... so it might be a hardware issue and not OS.

Looking at another thread (archived) I typed the commands they requested, can anyone detect a possible fix.

```

tuskpc@tuskpc-desktop:~$ dmesg | tail
[  320.048557] Buffer I/O error on device sr0, logical block 18
[  320.048562] Buffer I/O error on device sr0, logical block 19
[  320.048566] Buffer I/O error on device sr0, logical block 20
[  322.486195] ISO 9660 Extensions: Microsoft Joliet Level 3
[  322.503744] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  322.503761] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[  322.503769] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  322.503780] end_request: I/O error, dev sr0, sector 116
[  322.503832] ISOFS: unable to read i-node block
[  322.503848] isofs_fill_super: get root inode failed


```

```

tuskpc@tuskpc-desktop:~$ cat /proc/interrupts
           CPU0       
  0:        172   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  3:          4   IO-APIC-edge    
  4:          4   IO-APIC-edge    
  7:          0   IO-APIC-edge      parport0
  8:          2   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:      23916   IO-APIC-edge      pata_via
 15:     132989   IO-APIC-edge      pata_via
 16:          0   IO-APIC-fasteoi   radeon@pci:0000:01:00.0
 20:          0   IO-APIC-fasteoi   sata_via
 21:     127438   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5
 22:       2869   IO-APIC-fasteoi   VIA8237
 23:       8307   IO-APIC-fasteoi   eth0
NMI:          0   Non-maskable interrupts
LOC:     185740   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0


```


```

tuskpc@tuskpc-desktop:~$ sudo lshw -C disk
[sudo] password for tuskpc: 
  *-disk                  
       description: ATA Disk
       product: MAXTOR STM332062
       vendor: Maxtor
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5QF4RW98
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009e7fe
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD A  DH-3H20A
       vendor: ATAPI
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom3
       logical name: /dev/cdrw3
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: YX13
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom3
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-W54E
       vendor: TEAC
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/dvdrw2
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.1C
       serial: [TEAC    CD-W54E         1.1C
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: OneTouch
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 0121
       serial: 2HAA2ATD
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=dc350aef
  *-disk
       description: SCSI Disk
       product: 5000AAK External
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: 1.06
       serial: E
       size: 2TiB (2199GB)
       capabilities: partitioned partitioned:dos


```


```

tuskpc@tuskpc-desktop:/dev$ ls -al cdr*
lrwxrwxrwx 1 root root 4 2008-11-24 17:46 cdrom2 -> scd1
lrwxrwxrwx 1 root root 4 2008-11-24 17:46 cdrom3 -> scd0
lrwxrwxrwx 1 root root 4 2008-11-24 17:46 cdrw2 -> scd1
lrwxrwxrwx 1 root root 4 2008-11-24 17:46 cdrw3 -> scd0


```

---

### Post by Yezinki on 2008-11-25
Hi there,

I have a Matshita UJ- 846S DVD- RAM drive.....its a buggy & very choosy drive.

Wont even read media burnt on another optical drive.

My advice would be to use a lens cleaner CDROM & run it.

Probably a lens issue, helped me.

Good Luck.

Regards,

Yezinki.

---

