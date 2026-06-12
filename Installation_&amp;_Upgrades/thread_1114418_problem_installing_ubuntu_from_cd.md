---
title: "problem installing ubuntu from cd"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by nerdking on 2009-04-02
i have been using ubuntu for awhile i really like somethings about it, so im going to duel boot it on my new computer, how ever there is a problem during install, my hard drive does not show up on parttioner, if anyone could help i would really appreciate it.
heres my specs

Operating System 	  	System Model
Windows XP Professional Service Pack 3 (build 2600) 	  	BIOSTAR Group TP43D2-A7 6.0
Enclosure Type: Desktop
Processor a 	  	Main Circuit Board b
3.00 gigahertz Intel Pentium 4
16 kilobyte primary memory cache
1024 kilobyte secondary memory cache 	  	Board: BIOSTAR Group TP43D2-A7
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. 080015 07/15/2008
Drives 	  	Memory Modules c,d
250.05 Gigabytes Usable Hard Drive Capacity
183.25 Gigabytes Hard Drive Free Space

ASUS DVD-E818A3 [CD-ROM drive]
DIBUN B89A3GHYN4 SCSI CdRom Device [CD-ROM drive]
3.5" format removeable media [Floppy drive]

Seagate Barracuda 7200.10 ST3250410AS 250GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive - OEM

Installed Memory

Slot 'DIMM0' has 2048 MB (serial number SerNum00)
Slot 'DIMM1' has 2048 MB (serial number SerNum01)
Slot 'DIMM2' is Empty
Slot 'DIMM3' is Empty
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	250.05 GB 	183.25 GB free

---

### Post by Pumalite on 2009-04-02
Try adding 'all_generic-ide' to the boot parameters.
Also check your BIOS and see if you can make your drive AHCI
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

---

