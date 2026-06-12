---
title: "Dma + Asus A8n-e + Matsushita Sw-9585"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by rlgc79 on 2006-03-03
Hi,

I've got an Asus A8N-E (Nvidia Nforce 4 Ultra) with a SATA HD and a Matsushita SW-9585 DVD-Burner.  I've managed to enable DMA for the DVD-Burner, however I get all kind of errors whether I try to read or burn a CD/DVD. When the DMA is disabled everything runs smoothly.

Example:
 hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

test@x32:~/test/DVD$ cp -r /media/cdrom/* .
cp: reading `/media/cdrom/video_ts/video_ts.vob': Input/output error
cp: reading `/media/cdrom/video_ts/vts_01_0.bup': Input/output error
 --------------------------------------------------------

I don't think this is an Ubuntu specific problem. I've had problems with other distributions as well. Actually, in most distributions I have tryed, I need to install Linux in safe mode, otherwise I get random errors when the computer reads the CD.

The CD-Burner is okay, since on Windows DMA is on and everything works well. 

Any clue?

---

### Post by el3ktro on 2006-03-03
Which chipset does your mobo use?

Tom

---

### Post by rlgc79 on 2006-03-03
[QUOTE=el3ktro]Which chipset does your mobo use?

Tom[/QUOTE]

It's an Nvidia NFORCE 4 Ultra  (Socket 939)

---

### Post by rlgc79 on 2006-12-25
In case someone faces similar problems, I posted a workaround here: [http://www.ubuntuforums.org/showthread.php?t=325173](http://www.ubuntuforums.org/showthread.php?t=325173)

---

