---
title: "Looking to build a new machine"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by cprofitt on 2007-04-10
Hello all:

I am looking to potentially build a new machine -- I am aiming at the E6x00 series processors from Intel and a P965 motherboard...

Are there any "gotchas" there?

What video cards would you suggest?

What sound cards would you suggest?

Thanks.

---

### Post by volksolwagen57 on 2007-04-11
Great!! Intel has got AMD benchwarming and not benchmarking! ha ha good pun ;-D..
anyway, these are my suggestions:
an LGA775 board with the highest front side bus speed that you can get to make it future proof (like the evga 680sli with 1333mhz yeah!) 
try to get something real close to 1000mhz and you're good
i'm not sure if ubuntu has support to run in sli mode for gaming or graphics intensive applications like video editing and such BUT, at least get a motherboard that has an nvidia northbridge so it could run faster when you get an **nvidia graphics card**
additionally, i suggest a board that has a **pci-e** rather than **agp**. it's faster and you get more performance from a lower end (cheaper) graphics card than the hottest g card using agp.
the graphics card is all up to you. get NVIDIA-->there's more support with ubuntu, or any other linux distro, than ATI
i know this from experience. i'm fairly new to linux but i've always been a gamer. i had an ATI Radeon 9550 graphics card. i installed cedega and installed battlefield 2 and it would not run.
as for sound, if you just like to listen to music and have your computer make sounds for processes and stuff, get something cheap (generic)
if you like to play movies or make your own, get something with surround
if you're a gamer like me get a Fata1ity 7.1
stay with the Creative brand
good luck! :-)

---

### Post by uputer on 2007-04-17
> **PrivateVoid said:**
> Hello all:

I am looking to potentially build a new machine -- I am aiming at the E6x00 series processors from Intel and a P965 motherboard...

Are there any "gotchas" there?

What video cards would you suggest?

What sound cards would you suggest?

Thanks.
PrivateVoid, just search the site.    Put in the search terms, "P965" or "775" and see what you get.   I believe there was an issue with Intel's chipset boards, so either 975x or P965, but with the JMicron controller.    Since Intel decided to not support PATA anymore, the JMicron controller was used for dual SATA/PATA support?

Anyway, you can read about it and read about the related posts.   I am still not sure if they (i.e. kernel developers) have solved the problem as there is divided opinions on whether it's currently working.   I think it might depend on which kernel you're using and which version of the distro.   

The more recent distro has been reported to work but keep this in mind if you get a P965 board.   You will need to figure out which version to use and also know that this is applicable to all distros.

---

### Post by Unbound Spectre on 2007-04-17
Like volksolwagen57 suggested, get whatever nvidia card suites your needs.

I'm not sure what your sound needs are. If you don't care about having the best quality you can just use whatever sound comes onboard the motherboard. If quality is a concern and you are going to use an analog system, I would recommend an AuzenTech X-Meridian. If you change the OpAmps to some LM4562NA-ND's, you will get quality, accurate sound. You can read about it here. [http://www.avsforum.com/avs-vb/showthread.php?t=792354](http://www.avsforum.com/avs-vb/showthread.php?t=792354)

I unfortunately can't comment on how well it works in linux as I am still waiting for mine.

If there is anymore information you want, take a look at these sites.
[http://anandtech.com/](http://anandtech.com/)
[http://www.silentpcreview.com/](http://www.silentpcreview.com/)

---

### Post by dbd on 2007-05-20
> **volksolwagen57 said:**
> 
if you're a gamer like me get a Fata1ity 7.1
stay with the Creative brand
I didn't think the X-fi card's worked at all in Linux because of lack of drivers, am I wrong?



> **Unbound Spectre said:**
> I unfortunately can't comment on how well it works in linux as I am still waiting for mine.
Got it now? What do you think?

---

### Post by cprofitt on 2007-05-31
Would love to see more on this...

I went with the following system:

 [LIST=1]
[*]Intel BOXDP965LTCK LGA 775 Intel P965 Express ATX Intel Motherboard
[*] EVGA 320-P2-N811-AR GeForce 8800GTS 320MB 320-bit GDDR3 PCI Express x16 HDCP Video Card
[*]Intel Core 2 Duo E6600 Conroe 2.4GHz 4M shared L2 Cache LGA 775 Processor
[*]mushkin 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory
[*]2x  Seagate Barracuda 7200.10 (Perpendicular Recording) ST3250620AS 250GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive
[*]SAMSUNG Black 18X DVD+R 8X DVD+RW 8X DVD+R DL 18X DVD-R 6X DVD-RW 12X DVD-RAM 16X DVD-ROM 48X CD-R 32X CD-RW 48X CD-ROM 2MB Cache IDE DVD Burner with LightScribe and Software
[/LIST]

I am currently running Windows Vista so I can complete a programming project, but will switch to Ubuntu when the project is done.

---

