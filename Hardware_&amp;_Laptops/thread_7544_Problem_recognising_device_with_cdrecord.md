---
title: "Problem recognising device with cdrecord"
date: 2004-12-08
forum: Hardware &amp; Laptops
---

### Post by brewboy on 2004-12-08
Hi

I recently installed Ubuntu 4.10, and am very happy with the distribution. However, I am trying to write an iso image to cd using cdrecord. When I try to get the device details using 'cdrecord -scanbus', I get the following output:

Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

Apparently, there is a problem with the SCSI emulation for IDE devices. After some searching on the web, I have tried the following
1. Adding 'hdc=ide-scsi' to the kernel line for grub. However, this gives me the same results as before. 

2. Specifying 'ATAPI' as a device for cdrecord:

$ cdrecord -scanbus dev=ATAPI

Which gives: 
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related libscg interface code is in pre alpha.
Warning: There may be fatal problems.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.

And so on. 

If anyone has any experience of this or any advice about how I might be able to get past this I would be very grateful.

Thanks in advance

Simon

---

### Post by randy on 2004-12-08
The scanbus no longer works.  If you need to specify a device you can use the device node.  For my burners I use dev=/dev/hdc or dev=/dev/sr0

---

### Post by az on 2004-12-08
You will need to get rid of the hdc=ide-scsi, too as that is for oler linux kernels.

---

### Post by brewboy on 2004-12-09
Thanks to both of you for your help. 

I have deleted the 'hdc=ide-scsi' line and have tried to use cdrecord with dev=/dev/hdc. However, I get

scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
cdrecord: No such file or directory. Cannot open '/dev/hdc'. Cannot open SCSI driver.

I do not have a /dev/sr*, or any other /dev/s* devices listed. 

Using cdrecord with dev=help lists the following transport names: sg, pg, ATA, ATA (with sg interface) and RSCSI. 

Sorry to have to ask again, but I'm stuck on this. Does anyone have any clues?

Thanks
Simon

---

### Post by randy on 2004-12-09
Instead of hdc you need to post your device name.  hdc is the master drive on the second channel.  You also will need to be root.

---

### Post by mtber on 2004-12-09
I was having the same problem and this worked for me:

Edit /etc/default/cdrecord so that 

CDR_DEVICE=cdrw, 

then add cdrw to device listings as such. 

cdrw=/dev/hdd/  (and specify the other options for your drive)

Then, from the cli, 'cdrecord -prcap' recognizes the drive and for burning, 
'cdrecord dev=cdrw' works as well.   

Hope this helps.

---

### Post by brewboy on 2004-12-10
Thanks again for your replies and your time. I have found a temporary solution which allows me to use cdrecord. However, it is not yet perfect! 

I tried adding the suggested lines to /etc/default/cdrecord and adding a device as suggested above, but then realised that there was no /dev/hdc

The output of dmesg |grep hdc gave me:
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
hdc: SAMSUNG CDRW/DVD SM-332B, ATAPI CD/DVD-ROM drive
ide-cd: ignoring drive hdc

As this device point wasn't given, I then tried loading the modules for scsi emulation by hand (sg and ide-scsi)

With these modules, I can now use /dev/sr0 as the device point for my cd-writer. e.g.:
cdrecord dev=/dev/sr0 -data data_1.iso

However, in doing this I have lost the mount point for the cd. This I hope will be easier to solve than the problem of the writer!

Thanks for all replies, and I hope this may help some-one else.

Simon

---

