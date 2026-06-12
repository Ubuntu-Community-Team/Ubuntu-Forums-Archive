---
title: "SATA DVD burner won't burn"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by renai42 on 2007-09-05
hi there,

I just replaced my old IDE dvd burner with a new sata variety. It shows up fine in Ubuntu and will automatically mount CDs if you insert them.

Only problem is, when I try to use any DVD burning application, I get this error:

:-[ MODE SELECT failed with SK=5h/ASC=A8h/ACQ=04h]: Input/output error

Can anyone tell me what's going on? Feisty Fawn, very recent install, I know the SATA parts of my motherboard are compatible because I also have a SATA hard drive I've used for yonks.

Ideas?

Cheers,

Renai

---

### Post by DodDods on 2007-09-06
My lenovo sata burner do the same :sad:

---

### Post by jabster on 2007-09-14
A reply and a question.

Ok. I WAS having this same problem with a newly installed Asus DRW-1814BLT.

I was actually going to say I was having the same problem, and went to go try the burn again so that I could copy the error message and debugging info, and, lo and behold, it worked. This morning I got an error, and tonite it works. Haven't touched the computer all day except to check email about 10 minutes ago.

Actually, not quite true. I changed the K3B theme to the original theme after the failed burn this morning. I've even left K3B running all day to remind me to post a question about this.

Here's the situation: I've been running Feisty for a while, and decided to put in a new SATA DVD burner. BIOS recognizes it, I can mount and read discs, but I could not burn to it. K3B even recognizes the drive and whether or not there is a disc in there.

Just to check the drive, I booted into a live sesson of the latest Gutsy (tribe 5), and it worked just fine, so I figured it was some kind of hardware upgrade/installation problem.

Now I don't know what's going on.

Anybody got any idea why I can suddenly burn with this drive?

thanks,
john

---

### Post by jabster on 2007-09-14
OK

Wierd.

I just checked.

I set the K3B theme back to the new default theme, and I get an error. I then changed the theme back to the original K3B theme, and it burned.

How can a theme affect burning?

-john

debugging info:
> System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.7
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
ASUS DRW-1814BLT 1.13 (/dev/scd0, /dev/sg0) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

_NEC DVD_RW ND-3500AG 2.16 (/dev/hdd, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]
K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.2

mkisofs
-----------------------
/usr/bin/genisoimage: 
Short read on old image
/usr/bin/genisoimage: Short read on old image

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 0,12072 -prev-session /dev/scd0 -gui -graft-points -print-size -quiet -volid start -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-johnj/k3bOOrrhc.tmp -rational-rock -hide-list /tmp/kde-johnj/k3be3GsOb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-johnj/k3berS11a.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-johnj/k3bfAVjJb.tmp 

msinfo
-----------------------
0,12072

msinfo command:
-----------------------
/usr/bin/wodim dev=/dev/scd0 -msinfo 

---

### Post by clockworks on 2007-09-23
> **renai42 said:**
> Only problem is, when I try to use any DVD burning application, I get this error:

:-[ MODE SELECT failed with SK=5h/ASC=A8h/ACQ=04h]: Input/output error
Same problem, Lite-On LH-20A1S and Kubuntu 7.04 Feisty.

```

$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
```

---

### Post by Lampi on 2008-04-04
> **clockworks said:**
> Same problem, Lite-On LH-20A1S and Kubuntu 7.04 Feisty.
Well well - look at this - I'm using the same device and I still have problems burning DVDs using K3b on Kubuntu 7.10 Gutsy Gibbon.

The strange thing is: burning DVD-R Rewritables **sometimes** works if I apply a complete sequential format to the disc before the burning. I **never** sucessfully burned a DVD recordables so far with this device, it would not pass the integrity check I always apply after burning a DVD.

As far as I can tell it is NOT wise to burn DVDs **fast** using this device under linux, even if the recordable might support fast burning.

Secondly there is a firmware upgrade available for the LH20-A1S device you can download and install using windows, if you visit the lite-on-it global site. It might be a good idea to try this one out, altought it didn't help me burning under Gutsy Gibbon.

Maybe some of the tools k3b currently uses aren't working so perfect with this device, I simply don't know what's the problem is under linux, it works fine using Nero under Windows...

I hope it's just a matter of time until a fix will solve these problems. Maybe Hardy already ships some fixes for that problem - who kows...

---

### Post by thirdwheel on 2008-05-06
Hey,

I think I have a solution.

I have a LG SATA DVD burner connected to a SATA to IDE adapter.  Ubuntu automatically turns SCSI emulation on for all IDE drives.  When I had this plugged into my test machine (running Xubuntu 7.10) it gave the same error that the OP experienced.

I moved the drive to my devel machine (LFS 6.3, no SCSI emulation in the kernel) and it took right off.  My guess is that the SCSI emulation is getting in the way.  If there's a way to turn it off just for the burner and have it exist as an IDE device (i.e. /dev/hdc as opposed to /dev/scd0) that may solve the problem.

---

### Post by Estepario on 2008-06-06
i have the same problem... any news??

---

