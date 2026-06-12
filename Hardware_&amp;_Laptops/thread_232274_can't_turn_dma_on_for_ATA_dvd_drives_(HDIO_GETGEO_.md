---
title: "can't turn dma on for ATA dvd drives (HDIO_GETGEO failed)"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2006-08-08
Hi,

I'm helping someone I know in real life so I don't have constant acces to his machine. He's new to Ubuntu and his english isn't very good. 

**Problem description :**
- When I question hdparm I get " HDIO_GETGEO failed: Inappropriate ioctl for device"
- I can't turn dma on for my (ATA) dvd-rom and dvdrw drive.
- I believe (not sure) his dvd-drives should be available at /dev/hdX and /dev/hdY instead of /dev/scd0 and /dev/scd1 since they are ATA (not SATA).

Let's elaborate. Both /dev/scd0 and /dev/scd1 give the same results :

```

$sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)


$sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

$sudo hdparm -c1 /dev/scd0

/dev/scd0:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)

$sudo hdparm -c3 /dev/scd0

/dev/scd0:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)

```

**Things I tried :**

I tried setting the acces mode for the drives to : auto,large,LBA and CHS in my bios for both drives. These are the only relevant bios settings I found.

I added piix and ide-core to /etc/modules.
```

$ lsmod | grep piix
piix                   11652  0
ata_piix               11364  11
libata                 83440  1 ata_piix

$ lsmod | grep ide
video                  16324  0
video_buf              22724  2 saa7134_alsa,saa7134
videodev               10144  2 saa7134,ov511
ide_generic             1504  0

$ sudo modprobe ide-core
FATAL: Module ide_core not found.

```

**Some information about his system :**

Packard Bell 
PB14208886
IXTREME GOLD H5425

```

$cat /etc/modules
lp
psmouse
sbp2
piix
ide-core

```

/dev/scd0 on /media/cdrom-1 :
Lite-on SOHD-167T 48x CD-ROM /16x DVD

/dev/scd1 on /media/cdrom0 :
NEC ND-3500A DVDRW DL-station

Both are connected using ATA. So I'm not using SATA for them.
```

$lspci 

0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon X600(RV380)
0000:02:00.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
0000:02:01.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev f0)
0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

Thank you very much for your suggestions on advance.

PS : His english isn't very good. That's why we have also created a thread on the dutch forums here : [http://forum.ubuntu-nl.org/topic/2560](http://forum.ubuntu-nl.org/topic/2560)

---

### Post by ubuntu_demon on 2006-08-09
I forgot to mention that he has a P4 and he's running the linux-686 kernel.

I opened his case and I'm sure the dvd-drives are connected using ATA. It's a bit strange Ubuntu sees them as /dev/scd0 and /dev/scd1 instead of /dev/hdX and /dev/hdY.

(he's on vacation right now)

---

