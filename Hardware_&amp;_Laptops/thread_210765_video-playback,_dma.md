---
title: "video-playback, dma"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by AndiB. on 2006-07-07
I have a problem concerning my dvd-drive

my maschine:
- Intel Centrino Duo T2300 (laptop)
- Sony DVD DW-Q58A
- kernel 2.6.15-23-686

symptoms: 
- dvd playback is choppy even under windows xp
- when I burn dvds with k3b the speed varies a lot from 1x - 9x (I don't know if this is something bad...)

I tried:
- to enable DMA, but hdparm -d1 /dev/scd0 gave me

setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

- hdparm -a8 /dev/scd0 but it didn't solve my problem.

- under win xp everything works fine now after I reinstalled the ide controller. If you do this, win lets you enable dma 
([http://www.chip.de/c1_forum/thread.html?bwthreadid=672086](http://www.chip.de/c1_forum/thread.html?bwthreadid=672086) -- german)

- with knoppix 5.0.1 (Linux Kernel 2.6.17 (rc))  hdparm -i /dev/hdc:

/dev/hdc:

 Model=SONY DVD+/-RW DW-Q58A, FwRev=UDS1, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

So here dma is active. I cannot test if dvd playback works here b/c I booted from cd. Under Kubuntu hdparm -i /dev/scd0 fails.



So, and here I am. Is there any solution that does not involve a new kernel. Thanks for your help.

AndiB.

---

### Post by BuffaloX on 2006-07-07
The DMA option is mostly to lower CPU usage, it dosn't make the drive any faster.
If your system worked like it should, it should work both with and without DMA.

PS
For DVD playback your graphics must be accelerated.

---

### Post by AndiB. on 2006-07-07
Thanks for helping, BufalloX.

I'm not an expert, but I think my 1,6 Ghz should be enough for simply watching dvds. To me, it's seems like the data from the dvd-drive does not get fast enough to its destination (ram?). It's not that the drive, the cpu or the ram is too slow , it's just the connection between them. 

As I mentioned I had the same problem with same machine runnig under win xp. After I fixed dma, dvd playback was fine. But I would rather use linux...

---

### Post by dashnak on 2006-07-07
> **BuffaloX said:**
> PS
For DVD playback your graphics must be accelerated.

Errrmmm.... I don't really think this is true.... At all....
About DMA, it means "Direct Memory Access" and what it does is that the data from the drive "goes straight" to memory, instead of going through the CPU. This, of course, makes data transfer a whole lot faster.

---

### Post by cracker on 2006-07-07
Do video files on the hard drive play properly? This would narrow it down directly between the DVD drive or video playback in general.

---

### Post by AndiB. on 2006-07-08
Yup, this is how I do it now. After I copy the DVD to harddrive videos play nice and smoothly.

---

### Post by BuffaloX on 2006-07-09
> **dashnak said:**
> Errrmmm.... I don't really think this is true.... At all....
About DMA, it means "Direct Memory Access" and what it does is that the data from the drive "goes straight" to memory, instead of going through the CPU. This, of course, makes data transfer a whole lot faster.

Yes it makes transfers faster, but only from the buffers to the RAM, and the CPU dosn't have to manage the transfer to RAM, thus freeing some CPU resources. But it dosn't make the actual read of surface any faster.

Jerky playback of DVDs are more likely to be caused by bad disks, bad drives or Hardware conflicts. Most common hardware conflict is with audio or USB.

All this said, DMA transfer may help solve the symptom, but will not solve the basic problem.

Try disabling unused hardware in CMOS, like printer port. serial ports firewire, unused USB, onboard LAN, Onboard Audio.
Remember only disable those you do NOT use.

---

### Post by dashnak on 2006-07-09
Yeah, I agree with you, the part I was saying wasn't true was the " For DVD playback your graphics must be accelerated" bit.

---

### Post by BuffaloX on 2006-07-09
OK I see. ;) 

It dosn't need 3D of course, but the vesa driver didn't cut it for me, on a system I had earlier.

---

