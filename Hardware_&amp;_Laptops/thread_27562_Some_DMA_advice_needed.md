---
title: "Some DMA advice needed"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by denzilla on 2005-04-16
As some of you may have read, I added a DVD-ROM and a floppy drive to by ubuntu box a few days ago. I've got them working okay except that the DVD movie playback is somewhat choppy. I was informed that it could be a DMA issue, but I don't know enough to correct it. It appears that in the hdparm.conf that DMA is working for the CD-ROM, but no listing that I see for the DVD-ROM at all. Here is the file"

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}


What changes do I need to make, if any and where? Thanks all :)

I have the following hardware installed:

1 Hard Drive
1 floppy
1 CD-ROM
1 DVD-ROM

---

### Post by hagman on 2005-04-16
Hi,

just add 

/sbin/hdparm -d1 /dev/hdc (or /dev/hdd ... according to your drive(s))

to your /etc/init.d/bootmisc.sh somewhere before ":exit 0" and reboot.

Cheers,

Helge

---

### Post by denzilla on 2005-04-16
I added it like this, but no effect :(

#
#	Remove ".clean" files.
#
rm -f /tmp/.clean /var/run/.clean /var/lock/.clean

/sbin/hdparm -d1 /dev/hdd      ***** Added line***** 

: exit 0

---

### Post by hagman on 2005-04-16
Try "hdparm /dev/hdd" to check the actual settings.
If you see a line " using_dma    =  1 (on)".

Just to be sure: /dev/hdd is you DVD drive?

---

### Post by denzilla on 2005-04-16
[QUOTE=hagman]Try "hdparm /dev/hdd" to check the actual settings.
If you see a line " using_dma    =  1 (on)".

Just to be sure: /dev/hdd is you DVD drive?[/QUOTE]

Yea, I checked it with fstab beforehand.

---

### Post by hagman on 2005-04-16
What does "hdparm /dev/hdd" say?

---

### Post by denzilla on 2005-04-16
/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

and fo the cdrom:

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


This is weird because the hdparm.conf says dma is on for the cd

#/dev/cdroms/cdrom0 {
# dma = on
# interrupt_unmask = on
# io32_support = 0
#}

---

### Post by hagman on 2005-04-17
Not really. 

> #/dev/cdroms/cdrom0 {
# dma = on
# interrupt_unmask = on
# io32_support = 0
#} 

All entries are commented out. You have to remove the hash sign at the beginning of every line.

But for your DVD, DMA is switched on, so insert a DVD and check the drive speed by typing "sudo /sbin/hdparm -tT /dev/hdd" and watch the results.
You should see something like this:

> /dev/hdd:
 Timing cached reads:   1088 MB in  2.00 seconds = 545.17 MB/sec
 Timing buffered disk reads:   12 MB in  3.15 seconds =   3.80 MB/sec

(The exact values may vary depending on your system)

---

### Post by denzilla on 2005-04-17
/dev/hdd:
 Timing cached reads:   648 MB in  2.00 seconds = 323.89 MB/sec
 Timing buffered disk reads:    8 MB in  3.94 seconds =   2.03 MB/sec


Question:

Should I uncomment all the lines or just the DMA line?

When I run hdparm -I /dev/hdd  I get this out put:

root@ubuntu:/home/jr # hdparm -I /dev/hdd

/dev/hdd:

ATAPI CD-ROM, with removable media
        Model Number:       IDE DVD-ROM 16X
        Serial Number:
        Firmware Revision:  V1.06
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns


Does the * beside udma2 indicate what mode its operating in or just what dma its capable of?

---

### Post by hagman on 2005-04-17
[QUOTE=denzilla]/dev/hdd:
Should I uncomment all the lines or just the DMA line?[/QUOTE]
Yes. Uncomment the whole logical group.

[QUOTE=denzilla]Does the * beside udma2 indicate what mode its operating in or just what dma its capable of?[/QUOTE]
Yes, that's right.

---

### Post by denzilla on 2005-04-17
Okay, I uncommented everything. Neither the CD-ROM or the DVD Drive is dma at this point. I noticed this before uncommenting the hdparm.conf. Here is whats indicated now:

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

Funny thing is if I sudo hdparm -d1 /dev/hdd it says it enables DMA without error and DVD playback is smooth, but it goes back to non-DMA after reboot.

Could this issue be caused by both Drives operating on the same IDE channel? I figured it wouldn't be an issue since they're both udma2 rated.


*[COLOR=Red]update[/COLOR]* I've got DMA working on both drives now :) I added these to the bootmisc.sh:

/sbin/hdparm -d1 /dev/hdd
/sbin/hdparm -d1 /dev/hdc

I added this before as you suggested, but for some reason, they didn't affect anything, so I removed them (was afraid they would cause a problem later after I forgot I made the changes). They worked this time :) 

Thanks for all you help and I appreciate you sticking with me to fix the problem this long.

---

