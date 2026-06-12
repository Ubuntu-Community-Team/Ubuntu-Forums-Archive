---
title: "slow DVD burning (reading and writing)  yet DMA seems enabled"
date: 2010-10-26
forum: Hardware
---

### Post by cspadijer on 2010-10-26
Hi guys.
Any insight into why reading and writing(burning) a DVD is so slow?
Seems to be running at UDMA/100.
In the past the problem has normally been DMA not being enabled.

Details:

sudo hdparm -tT /dev/sr0
/dev/sr0:
 Timing cached reads:   1656 MB in  2.00 seconds = 828.13 MB/sec
 Timing buffered disk reads:    8 MB in  3.85 seconds =   2.08 MB/sec

dmesg | grep scsi

[    1.340292] scsi3 : ahci
[    2.421245] scsi 2:0:0:0: CD-ROM            hp       DVDRAM GT30L     mP04 PQ: 0 ANSI: 5
[    2.423390] sr0: scsi3-mmc drive: 62x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.423524] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.423597] sr 2:0:0:0: Attached scsi generic sg2 type 5

dmesg | grep ata

[    1.096299] ata2.00: ATAPI: hp      DVDRAM GT30L, mP04, max UDMA/100
[    1.112276] ata2.00: configured for UDMA/100

Option 1# I tried:
added to /etc/hdparm.conf

/dev/sr0 {
    dma = on           
}

Option 2 I tried:
added the following to /etc/modprobe.d/aliases

## Turn on DMA for DVD ############################
alias ata_generic off
alias pata_atiixp on

Option 3 I tried:

added the following to /etc/modules
sata_sil
piix
ide-core

Option 4 I tried:
sudo hdparm -d1 /dev/sr0

/dev/sr0:
 setting using_dma to 1 (on)

Option 5 I tried:
added the following to /etc/initramfs-tools/modules

pata_atiixp
blacklist ata_generic

Then ran sudo update-initramfs -u

Option 6 I tried:
Tried changing the BIOS to IDE instead of EHCI... No dice.

Still slow
:confused:

Ubuntu 10.10
2.6.35-22-generic-pae

---

