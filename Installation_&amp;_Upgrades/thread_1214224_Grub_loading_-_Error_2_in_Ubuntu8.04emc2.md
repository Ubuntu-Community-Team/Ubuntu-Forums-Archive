---
title: "Grub loading - Error 2 in Ubuntu8.04/emc2"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2009-07-15
I'm trying to instal 8.40/emc2 from a downloaded disk . I tried out the live CD while waiting for a larger hdd to arrive, and that worked fine, but I didn't try to install it (the old one was only 2Gb).

The new set up is a Gigabyte GA-5AX board, AMD K-6/500, with 512Mb RAM,Ati video card, Seagate 20Gb hdd.

The hdd is currently set as "Normal" in the bios, and I've tried, after installing and getting stuck, to then change the boot up order from cd/hdd/A to hdd/cd/A, but no difference.

I've checked that the hdd is master, and the cdrom is slave.

I have been installing with the primary partition at 3000Mb, following a set of guidance notes on Softpedia web site, but looking at other "cries for help", I see several suggestions of making the primary partition much smaller.
I tried 500mb, but Ubuntu didn't want to know, so I upped it 2000Mb, and still no go.
I'm now back to square one, and am now trying 3000mb for root and home, 1024Mb for swap, and leaving the rest free.
Any advice, or better still a solution would be most welcome.

John

---

### Post by grey1beard on 2009-07-15
Cracked it  :)

The bios showed two different "versions" of the hdd.
On the page that shows the primary/secondary master/slave info, I switched the hdd type to Normal, but on the Auto detect hdd page it showed the drive as LBA.
So I went back to the first page and changed the setting to LBA, and re booted.
Bigo.
I've no idea what all the above means, but I hope it may help someone else.
John

---

