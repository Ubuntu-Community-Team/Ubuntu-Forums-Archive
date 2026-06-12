---
title: "UNR .img don't work"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by amadeus.ch on 2009-07-10
Hello

Is it possible that the ubuntu-9.04-netbook-remix-i386.img has a wrong partition table?
It was not possible for me to boot  from this image on a usb-stick. I have tried several sticks! I used dd, usb-imagewriter und unetbootin. The MD5 hash is ok. 

If I mount this image and list with fdisk the partition tabel - the are so stange entrys.

What can I do to? I will install the UNR on my Shuttle X50!

root@fry:~# kvm-nbd --connect=/dev/nbd0  /home/amadeus/Desktop/ubuntu-9.04-netbook-remix-i386.img
root@fry:~# mount /dev/nbd0 /mnt/
root@fry:~# ls /mnt/
autorun.inf  casper  dists  install  md5sum.txt  pics  pool  preseed  README.diskdefines  syslinux  wubi.exe
root@fry:~# fdisk -l /dev/nbd0

Platte /dev/nbd0: 992 MByte, 992837632 Byte
255 Köpfe, 63 Sektoren/Spuren, 120 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x8ef631df

Das sieht nicht wie eine Partitionstabelle aus.
Sie haben wahrscheinlich das falsche Gerät ausgewählt.

     Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/nbd0p1   ?      131500      253426   979374166   66  Unbekannt
Partition 1 hat unterschiedliche phys./log. Anfänge (nicht-Linux?):
     phys=(734, 123, 14) logisch=(131499, 73, 31)
Partition 1 hat unterschiedliche phys./log. Enden:
     phys=(120, 143, 6) logisch=(253425, 186, 53)
Partition 1 endet nicht an einer Zylindergrenze.
/dev/nbd0p2   ?      214713      460236  1972168331    7  HPFS/NTFS
Partition 2 hat unterschiedliche phys./log. Anfänge (nicht-Linux?):
     phys=(187, 180, 14) logisch=(214712, 73, 61)
Partition 2 hat unterschiedliche phys./log. Enden:
     phys=(784, 0, 13) logisch=(192886, 138, 21)
Partition 2 endet nicht an einer Zylindergrenze.
/dev/nbd0p3   ?      204159      325757   976730017   7d  Unbekannt
Partition 3 hat unterschiedliche phys./log. Anfänge (nicht-Linux?):
     phys=(252, 59, 46) logisch=(204158, 244, 37)
Partition 3 hat unterschiedliche phys./log. Enden:
     phys=(139, 118, 4) logisch=(58406, 222, 40)
Partition 3 endet nicht an einer Zylindergrenze.
/dev/nbd0p4   ?      260154      260672     4161550   6f  Unbekannt
Partition 4 hat unterschiedliche phys./log. Anfänge (nicht-Linux?):
     phys=(370, 101, 50) logisch=(260153, 61, 5)
Partition 4 hat unterschiedliche phys./log. Enden:
     phys=(10, 114, 13) logisch=(260671, 83, 4
Partition 4 endet nicht an einer Zylindergrenze.

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge


peace + be wild

---

