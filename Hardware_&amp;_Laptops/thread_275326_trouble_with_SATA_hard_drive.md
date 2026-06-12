---
title: "trouble with SATA hard drive"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by Joseph Elliott on 2006-10-11
Hi, I recently purchased a 250 gig SATA Samsung SpinPoint P120 SATA Series ( specs are at [http://www.samsung.com/Products/HardDiskDrive/SpinPointPSeries/HardDiskDrive_SpinPointPSeries_SP2504C.asp]("http://www.samsung.com/Products/HardDiskDrive/SpinPointPSeries/HardDiskDrive_SpinPointPSeries_SP2504C.asp")

Im using a gigabyte motherboard (specs at [http://www.dealtime.com/xPF-Gigabyte_VIA_KM400_SoA_AGP_8x_MATX_Audio_LAN~r-1~CLT-INTR~RFR-www.google.ca]("http://www.dealtime.com/xPF-Gigabyte_VIA_KM400_SoA_AGP_8x_MATX_Audio_LAN~r-1~CLT-INTR~RFR-www.google.ca")

I also have a 40 gig samsung PATA drive connected (with my original ubuntu installation)

power supply is 230 and ram is 256mb.  Im using on board video and sound etc.

Here is the problem,  I want to run the 250 gig by itself so that i can recover files from a 120 gig western digital.  However while the bios recognises the 250 gig it seems to freeze when i try to boot from it and if i try to run the ubuntu install cd it starts its live cd stuff, gets part way through booting then the video output seems to stop, my screen goes blank and the screen lights all start flashing.  If I hook up my 40 gig I can boot and do all the regular stuff,  when i access my partitions in this mode I says that my 250 gig is hda1, extended 3 file system, access path /, not formattable,232.62 gigs but only 19.7 gigs available.  it also says my 40 gig is hdc1, extended 3 file system, access path none, formattable, 36.69 gigs no space available.  Im not sure what else to include.

oh my motherboard doesnt have a SATA cable, im using a IDE device mini vertical bridge to connect to my PATA cable and power supply.

I was able to install to the 250 gig once while the 40 was also present but now I can no longer remove the 250 gig without causing the boot sequence in the 40 to fail.  Im not sure what happened there.  When i started the install cd it asked me to partition the 250, I said yes and selected the correct drive from the list and then it did its thing.

Thanks for any help.
Joseph

---

