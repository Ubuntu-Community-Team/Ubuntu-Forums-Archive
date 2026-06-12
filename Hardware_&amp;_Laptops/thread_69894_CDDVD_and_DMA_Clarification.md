---
title: "CD/DVD and DMA Clarification"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by InetWizard on 2005-09-28
Dear All,

I've been reading a number of posts about DMA not being enabled by default in Ubuntu and people experiencing choppy DVD playback etc. The directions for enabling DMA haven't worked for me in the past. I would get an error on boot refering to the path I specified not being found.

When I issue the following command it appears to tell me that UDMA is already enabled on my drive any way. Can anyone confirm this, or am I reading the output wrong? 

```

$ hdparm -i /dev/hdc

/dev/hdc:

 Model=PIONEER DVD-RW DVR-106D, FwRev=1.07, SerialNo=CEDL014139WL
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

```

With thanks. 

-Corey

---

### Post by Biased turkey on 2005-09-28
Hey, we are in 2005 aren't we ? :)
I wouldn't trust any 2005 Linux  distro that by default desable UDMA.
By your hdparm listing, you shouldn't worry because udma2 is enabled.

Just for the info, what chipset does your motherboard use ?

---

### Post by mlomker on 2005-09-28
> I've been reading a number of posts about DMA 


Are you running Hoary or Breezy (I ask because Breezy users frequently post in the Hoary forum without disclosing that).

It's quite possible that the IDE driver for your particular controller enables it by default.  That isn't the case for everybody's machine.

---

### Post by InetWizard on 2005-09-29
mlomker,

I'm running Hoary at the moment. I'm relatively new to Linux and so I haven't played with Breezy yet. I am looking forward to its official release though so I can start using it.

If UDMA is enabled by default. What could be causing the choppiness in playback I'm experiencing with DVD's? I'm using the libdvdcss package from the repositories, and also the NVIDIA driver from the repository. 

Any thoughts gratefully recieved. 

Biased Turkey,

I'm not sure what chipset my mainboard has. Is there anyway to find out without opening the case?

With many thanks for your assistance. 

-Corey

---

### Post by mlomker on 2005-09-29
> experiencing with DVD's? I'm using the libdvdcss package from the repositories, and also the NVIDIA driver from the repository. 


The next question I would ask is the video.  What performance are you seeing in **glxgears**?  It seems that you need a fairly good number for smooth playback.  I get over 2k on mine and I've never had a problem.

---

### Post by Biased turkey on 2005-09-29
[QUOTE=InetWizard]mlomker,

I'm not sure what chipset my mainboard has. Is there anyway to find out without opening the case?
With many thanks for your assistance. 
-Corey[/QUOTE]

What processor do you have ?
if you type the lspci command, the 1st line should tell you the chipset.

---

### Post by InetWizard on 2005-10-01
mlomker,

When running glxgears I get the following output. I've removed the GL_Extensions part for clarity. 

```

wallis@firebird:~$ glxgears -info
GL_MAX_VIEWPORT_DIMS=4096/4096
GL_RENDERER   = GeForce FX 5600/AGP/SSE2
GL_VERSION    = 1.5.3 NVIDIA 71.74
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = {...}
11091 frames in 5.0 seconds = 2218.200 FPS
13691 frames in 5.0 seconds = 2738.200 FPS
13608 frames in 5.0 seconds = 2721.600 FPS
2242 frames in 5.0 seconds = 448.400 FPS

```

The first 15 seconds was with the glxgears window in the default size, the last 5 seconds was the window maximised. 

Biased Turkey,

According to lspci my chipst is " Intel Corp. 82845G/GL[Brookdale-G]/GE/PE" which makes sense as it is an intel board, I just couldn't remember the chipset.

Interestingly this morning I installed xine from the repository and was able to successfully play DVD's. This suggests to me there may be something wrong with the way Totem is configured. In any case I'm quite happy using xine to watch DVD's.

Many thanks for your support in answering my questions, it is greatly appreciated. 

-Corey

---

### Post by tseliot on 2005-10-01
[QUOTE=InetWizard]Dear All,
I've been reading a number of posts about DMA not being enabled by default in Ubuntu and people experiencing choppy DVD playback etc. The directions for enabling DMA haven't worked for me in the past. I would get an error on boot refering to the path I specified not being found.
When I issue the following command it appears to tell me that UDMA is already enabled on my drive any way. Can anyone confirm this, or am I reading the output wrong? 
```

$ hdparm -i /dev/hdc
/dev/hdc:
Model=PIONEER DVD-RW DVR-106D, FwRev=1.07, SerialNo=CEDL014139WL
Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
BuffType=13395, BuffSize=64kB, MaxMultSect=0
(maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes:  pio0 pio1 pio2 pio3 pio4
DMA modes:  mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 *udma2
AdvancedPM=no
Drive conforms to: device does not report version:
* signifies the current active mode

```
With thanks. 
-Corey[/QUOTE]
sudo hdparm -d /dev/hdc is a faster way to do that (it tells you only whether your are using DMA or not).

Please try it and post the output (just to be 100% sure)

---

### Post by tseliot on 2005-10-01
[QUOTE=InetWizard]
Interestingly this morning I installed xine from the repository and was able to successfully play DVD's. This suggests to me there may be something wrong with the way Totem is configured. In any case I'm quite happy using xine to watch DVD's.[/QUOTE]
Open synaptic and install "totem-xine".

---

### Post by InetWizard on 2005-10-02
tseliot,

Many thanks for your alternate command to query about dma. The output of the command is as follows. 

```

$ sudo hdparm -d /dev/hdc

/dev/hdc:
 using_dma    =  0 (off)

```

This would seem to suggest that dma is indeed turned off. Which is odd because the earlier command seemed to imply that it was on. :confused: 

I seem to be able to turn on DMA for the drive using the following command

```

$ sudo hdparm -d 1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

```

Is there any way to do this at boot?

With thanks. 

-Corey

---

### Post by TristanMike on 2005-10-02
Absolutely, you'll have to edit the /etc/hdparm.conf and add ```
/dev/hdc {
	dma = on
}
```I put it just before "#command_line...." This should enable at boot.

---

### Post by InetWizard on 2005-10-03
TristanMike,

Many thanks for your tip on editing the /etc/hdparm.conf file. DMA is now enabled at boot time for my CD Drive. 

Many thanks to all of those who helped. 

-Corey

---

