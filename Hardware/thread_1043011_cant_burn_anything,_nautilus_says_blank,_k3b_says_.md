---
title: "cant burn anything, nautilus says blank, k3b says no media"
date: 2009-01-18
forum: Hardware
---

### Post by purefan on 2009-01-18
Hello everyone!

I've looked in these forums, looked in google and couldnt find anything useful for my situation, maybe someone could shed some light here..

I want to burn an ISO image, so I pop the blank cd in the drive, nautilus says its blank, go to K3b and he says "No Medium Present", so I give it a few seconds to see if it just hasnt noticed... nothing, couple of minutes, nothing. So I go to gnomeBaker which seems to find the cd, start the burning, finishes supposedly ok, it ejects it and I pop it in again, nautilus says blank cd, K3b keeps saying No Medium Present... so I try to burn with gnomeBaker once again except this time it fails...

here is the output from the second gnomeBaker try:
> 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-850S '
Revision       : '1.40'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
FIFO size      : 12582912 = 12288 KB
wodim: Cannot load media.


last line seems important: "wodim: Cannot load media". But I dont know what 'wodim' is or how to fix it, Im guessing its related to the K3b issue as well but what to do?

---

### Post by itix on 2009-01-19
If you type "man wodim" the linux manual will tell you what wodim is and it says
> NAME
       wodim - write data to optical disk media


Gnome-baker uses wodim for burning and is simply a GUI.

I have no idea really what the problem is though. Have you checked the "usual stuff" like if the cd really is blank, or if the CD is damaged or if the ISO is a DVD-iso and stuff like that. You might also wan't to check the integrity of the ISO.

---

### Post by purefan on 2009-01-19
Yeap I did all those things, even bought a new set of blank cds to make sure I wasnt picking the wrong ones (too old or scratched or whatever). Eventually got to burn at 1x with gnome-baker and one of the cds (1 out of 3) booted the ubuntu 8.10, ran the integrity test and it said it was fine, but then on the next restart it didnt boot, and its just random from then...

---

### Post by teaker1s on 2009-01-19
check drive manufacturer for new firmware:guitar: had similar before

---

### Post by purefan on 2009-01-20
im blaming it on the actual drive, this is a satellite pro from toshiba (L300D) and the drive is a Matshita something something... quite an odd number for which I couldnt really find anything, same with the webcam its a chicony odd number for which I couldnt ever find a driver, so since this is a spare machine I installed another operating system just to get the webcam at least...

Thanks to all anyways :) Next time I'll get a more branded and supported machine, I just went for the price here...

---

