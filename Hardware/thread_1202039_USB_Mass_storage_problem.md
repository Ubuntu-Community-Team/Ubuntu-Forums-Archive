---
title: "USB Mass storage problem"
date: 2009-07-01
forum: Hardware
---

### Post by led2010 on 2009-07-01
Hi !
I have been using a USB key (FAT32) 1without any problems for weeks, and I wanted to re-format it today. 
I used Gparted, but afer having processed, my key does't work anymore. Moreover, Gparted does not see it.
I have the following output with the command **fdisk -l** ;[INDENT]>  Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x149f149f

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1         637     5116671   83  Linux
/dev/sda2            2433       19335   135773347+  83  Linux
/dev/sda3           19336       19457      979965   82  Linux swap / Solaris[/INDENT]So I looked at the logs (messages, syslog) and I found some problems on /dev/sdb which is my USB mass strorage. It works as it is not regogmized by my system (Jaunty 32b, with a 2.6.28 kernel)[INDENT]> Jul  2 01:38:28 glagla kernel: [  464.108167] usb 1-1: reset high speed USB device using ehci_hcd and address 3
Jul  2 01:38:28 glagla kernel: [  464.240895] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  2 01:38:28 glagla kernel: [  464.240908] end_request: I/O error, dev sdb, sector 344
Jul  2 01:38:28 glagla kernel: [  464.240917] __ratelimit: 20 callbacks suppressed
Jul  2 01:38:28 glagla kernel: [  464.240924] Buffer I/O error on device sdb, logical block 43
Jul  2 01:38:28 glagla kernel: [  464.240934] Buffer I/O error on device sdb, logical block 44
Jul  2 01:38:28 glagla kernel: [  464.240942] Buffer I/O error on device sdb, logical block 45
Jul  2 01:38:28 glagla kernel: [  464.240949] Buffer I/O error on device sdb, logical block 46
Jul  2 01:38:28 glagla kernel: [  464.240956] Buffer I/O error on device sdb, logical block 47
Jul  2 01:38:28 glagla kernel: [  464.240963] Buffer I/O error on device sdb, logical block 48
Jul  2 01:38:28 glagla kernel: [  464.240970] Buffer I/O error on device sdb, logical block 49
Jul  2 01:38:28 glagla kernel: [  464.240977] Buffer I/O error on device sdb, logical block 50
Jul  2 01:38:28 glagla kernel: [  464.240984] Buffer I/O error on device sdb, logical block 51
Jul  2 01:38:28 glagla kernel: [  464.240991] Buffer I/O error on device sdb, logical block 52[/INDENT]I can't format it again  because it is not regognized by the usual system tools (parted, fdisk...)
Do you know how I could re-use my USB key ? 



Thanks

---

