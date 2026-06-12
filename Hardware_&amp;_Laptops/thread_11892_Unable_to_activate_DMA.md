---
title: "Unable to activate DMA"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by Scorpios on 2005-01-20
hey there,

I have a GA-7N400Pro2 mobo based on NForce2 chipset and AMD sempron 2600 cpu on it. Also i have a pair on IDE drives (WD 120G).

My problem is that i cannot bring the hdparm or the kernel to agree with me that those drives can use DMA, I just keep on getting the msg:

```
#su
#hdparm -d1 /dev/hda
/dev/hda:
 setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

```

The really wierd thing about this is this:

```
#su
#hdparm -I /dev/hda
#
/dev/hda:
 Model=WDC WD1200JB-00GVA0, FwRev=08.02D08, SerialNo=WD-WCALA1110578
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234439535
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version: 

 * signifies the current active mode

```

As you can see, the hd tells it is actually operates in udma5 mode

Does anyone know how to solve this problem? my hd's are so slow...

Scorpio

---

### Post by Scorpios on 2005-01-21
I have solved the problem!

I used kernel 2.6.8-k7 and when I boot using 2.6.8-686 i was able to activate the DMA.

Just curious, is this supposed to be that way? As far i know this problem is caused because the nforce2 chipset support is probebly compiled as module instead of being compiled into the kernel. Is this a "bug" or just an unnecessary feature?

Scorpio

---

### Post by wallijonn on 2005-01-21
Did the [COLOR=Red]hdparm -T /dev/hda[/COLOR] and [COLOR=Red]hdparm -t /dev/hda[/COLOR] scores change between the two kernels? I would think that since it is an AMD that you should be using the k7 kernel.

---

### Post by clarke.rainey on 2005-01-21
Yeah I was also wondering which kernel I should use being that I have an AMD 64, but I am running it in 32 bit...

---

### Post by Scorpios on 2005-01-21
yes, using the K7 kernel they were around the 2-3MB per sec and using 686 kernel around the 30-40MB. no apperent change with the buffer speed. This why i said it might be a problem in the k7 kernel configuration.

Scorpio

---

### Post by satyam on 2005-01-28
OK, so I'm having an identical problem with Ubuntu 64. Even though my hard disks and optical drives are all showing either mdma or udma capability, I can't seem to activate them. 
  If i understand the post correctly, it's because the ubuntu kernel that was shipped with the Warty Warthog doesn't support DMA? So where can I get a 64 bit kernel that does? Or should I try to recompile my existing kernel? 

  I'm using an AMD Athlon 64 3000+ on an MSI K8N Neo Platinum.

Thanks.

---

### Post by cuoog on 2005-01-28
Sorry for a bit of a me-too post, I'm in the same boat.

But I don't think the 686 kernel is a cure-all.  I was using the 386 kernel, then I switched to the k7, then I switched to the 686, and I couldn't use hdparm to activate dma in any of them.  I think I need to recompile to enable dma, but I'm still new to linux and I havent found a guide for doing it in Ubuntu.  anyone have any other ideas or know of a guide on how to do it?

(using an Athlon 64 3200+ with a SiS 755 chipset)

thanks,

dan

---

### Post by Scorpios on 2005-01-30
Hey

After some more digging, i have found that the module amd74xx might be the answer, not the kernel.

Try append it to /etc/modules file and run update-modules or reboot (i'm not sure update-modules will help) and then try hdparm again.

As i understood, this module is responsible for ide stuff using NForce2 (please correct me if i'm wrong). If that's the issue, and you are not using NForce2 chipset, try to find the module that works for your's.

I take back my claim about the kernel, I now belive it's not the problematic issue.

Scorpio

---

### Post by cuoog on 2005-01-30
Just tried a sudo modprobe amd74xx

did nothing for me, though after reading on what it doesn (should have done that earlier, eh?) it seems like it might be just the thing for all the nforce2 users out there.  When i try to modprobe any of the generic modules like ide-dma, I get an error that the module isn't installed.  Since I'm not aware of any chipset specific modules for all the SiS users out there, is there any way to get the generic DMA support other than to recompile the kernel?

---

### Post by satyam on 2005-02-02
OK, so I believe that I'm using the Nforce chipset. I think. Anyway, when I did a modprobe, the amd74xx module showed up, so it's loaded at startup.
  However, when I had checked the hdparm documentation, it indicated that at bootup, hdparm runs *before* the modules are loaded, so at bootup, all hdparm sees is the kernel itself. The documentation indicated how to change the startup order so that hdparm runs after the modules are loaded, but seemed to suggest that it's not 100% safe to do so. Even so, I tried it, and nothing doing.
  I looked at the configuration file in /boot, and it indicates that most of the dma tools are actually modular. I think that I'll have to try and recompile, but I need a walkthrough for that.
  I appreciate all the information I'm getting in this forum, thanks a lot.

---

### Post by satyam on 2005-02-04
Ok, I got the amd74xx module in the right place, and now I can activate DMA on my drives. hdparm returns some really low disk read rates, but the DMA seems to be working, since I can now watch a DVD and not miss frames.
  
Thanks a lot.

---

### Post by Scorpios on 2005-02-05
Hey

Try putting amd74xx module at the top of /etc/modules and run update-modules.

Also, try hdparm -iI /dev/... and check which dma modes your drive supportes. if it supports udma5 like most of the modern drives hdparm -t should return something around 50-60MB/sec.

Scorpios

---

