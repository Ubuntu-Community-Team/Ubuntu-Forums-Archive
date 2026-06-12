---
title: "mount: special device /dev/hdb does not exist...on laptop"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by kaplis on 2007-05-06
hey

the thing started on Mint and now it continue on Feisty...

CD/DVD room cant read my CD and DVD- it just start to read, then stop and nothing happens. it just started one fine day and i dont what has happened because i havent changed anything anywere.

System journal gives out-

Apr 30 20:32:18 kauluzagis kernel: [17179573.260000] hdb: \377, ATAPI UNKNOWN (type 31) drive
Apr 30 20:43:28 kauluzagis kernel: [17179573.280000] hdb: QSUS1 1 SCS-3434Q 1 1 1 1 1 1 1 1 1 1 1, ATAPI UNKNOWN (type 21) drive
Apr 30 21:55:54 kauluzagis kernel: [17179573.468000] hdb: ASUS SCB-2424A, ATAPI CD/DVD-ROM drive
Apr 30 21:55:54 kauluzagis kernel: [17179573.524000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 30 21:55:54 kauluzagis kernel: [17179573.832000] hdc: HTS421260H9AT00, ATA DISK drive
Apr 30 21:55:54 kauluzagis kernel: [17179574.504000] ide1 at 0x170-0x177,0x376 on irq 15
Apr 30 21:55:54 kauluzagis kernel: [17179574.532000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Apr 30 21:55:54 kauluzagis kernel: [17179574.532000] Uniform CD-ROM driver Revision: 3.20
Apr 30 21:57:52 kauluzagis kernel: [17179957.540000] hdb: ATAPI reset complete
Apr 30 22:03:30 kauluzagis kernel: [17180296.376000] cdrom: This disc doesn't have any tracks I recognize!
Apr 30 22:04:14 kauluzagis kernel: [17180340.148000] cdrom: This disc doesn't have any tracks I recognize!
Apr 30 22:10:06 kauluzagis kernel: [17179573.524000] hdb: QSUS1 1 SCS-3434Q 1 1 1 1 1 1 1 1 1 1 1, ATAPI UNKNOWN (type 21) drive
May  1 08:22:07 kauluzagis kernel: [    6.864000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
May  1 10:33:44 kauluzagis kernel: [    3.876000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
May  1 10:33:44 kauluzagis kernel: [    3.876000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
May  1 10:33:44 kauluzagis kernel: [    4.888000] hdb: QSUS0 0 SCR-2424Q 0 0 0 0 0 0 0 0 0 0 0, ATAPI UNKNOWN (type 21) dri

as you can see at the begining it worked occasionaly, now it doesnt work at all. BOIS shows my CD/DVD drive, but not Sysinfo 0.7, Hardinfo 0.4.1, K3b.

Searches in Ubuntu forums, Google and Linuxquestions.org hasnt given any clear evidence, except that i have to change my CD/DVD drive because its broken. when i get my laptop to service, they said that CD/DVD drive had red all discs they tried....

any ideas?

tnx

---

### Post by exoasol on 2007-05-08
i am experiencing the same issue with a desktop computer(or at least it seems the same)  I dont have a /dev/hd* or /dev/sd* (except for my hard drive which is sda)

---

### Post by DagMan on 2007-05-08
Mine is scd0 and was previously sg0 on another computer.
ls -l /dev/dv*
lrwxrwxrwx 1 root root 4 2007-05-08 15:38 /dev/dvd -> scd0
lrwxrwxrwx 1 root root 4 2007-05-08 15:38 /dev/dvdrw -> scd0

---

### Post by exoasol on 2007-05-09
i dont have /dev/dv* anything.  I used mknod to make hdc and still wont mount gives me /dev/hdc is not a valid block device

---

### Post by tthorb on 2007-07-02
Try:

sudo update-initramfs -u -k 2.6.22-7-generic

---

