---
title: "Can't rip DVDs"
date: 2009-02-19
forum: Hardware
---

### Post by tsmithtree on 2009-02-19
I'm running ubuntu 8.10 amd64, and my dvd ripping is horrendously slow. At first, DVD ripping would slow down my system to the point of being unusable, but I fixed that by disabling the ata_generic kernel module and enabling the correct sata drivers for my motherboard. So now I can rip DVDs, but the speed is VERY slow, it would take hours to complete one disc. I have no problems watching an entire dvd in mplayer, but I want to be able to rip dvds at the speed my drive is capable of doing. I tried the drive in a windows box, and it works fine. I also updated the drive's firmware, but my linux problems persist. It's not a problem with my kernel (a realtime patched kernel I compiled), since I tried it with the default kernel in the livecd environment and I got the same problem. I also tried it on both my motherboard's sata controllers (intel and jmicron), with the same results on each.

tried setting dma to on:
```
root@snorlax:/home/tsmith# hdparm -d1 /dev/sr0

/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```
Didn't seem to work, but it looks like dma is already enabled.

Here's the output of hdparm -i /dev/sr0
```
root@snorlax:/home/tsmith# hdparm -i /dev/sr0

/dev/sr0:

 Model=HL-DT-STDVD-RAM GH22NS30                , FwRev=1.01    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode


```
This looks like I have dma enabled, so why aren't my read speads higher?

some output from dmesg after I run hdparm -t /dev/sr0:
```

end_request: I/O error, dev sr0, sector 7688
Buffer I/O error on device sr0, logical block 1922
Buffer I/O error on device sr0, logical block 1923
Buffer I/O error on device sr0, logical block 1924
Buffer I/O error on device sr0, logical block 1925
Buffer I/O error on device sr0, logical block 1926
Buffer I/O error on device sr0, logical block 1927
Buffer I/O error on device sr0, logical block 1928
Buffer I/O error on device sr0, logical block 1929
Buffer I/O error on device sr0, logical block 1930
Buffer I/O error on device sr0, logical block 1931
end_request: I/O error, dev sr0, sector 7948

```
I don't know what this means. I thought it meant that something was wrong with the disc, but I get this with ALL discs I try (but with different block numbers).

```

root@snorlax:/home/tsmith# hdparm -tT /dev/sr0

/dev/sr0:
 Timing cached reads:   6186 MB in  2.00 seconds = 3094.53 MB/sec
 Timing buffered disk reads:    8 MB in  3.25 seconds =   2.46 MB/sec

```

2.4 mb/sec is much too slow, I tried it on another computer and got much faster speeds. It's not my hardware; I have a 3ghz intel quad core and 4gb ram. If it's useful, my motherboard is a gigabyte GA-EP45-UD3R/UD3. On a side note, don't ever buy a gigabyte board. I have bought two, big mistake, nothing but problems on both.

lspci, if it helps:
```

root@snorlax:/home/tsmith# lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)
01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

I know it's not a problem with the drive, the cable, the dvd ripping application, or the disc. That means that it's either a low-level software problem or something wrong with my motherboard, but since I tried both my SATA controllers it makes sense that it's a software issue.

Oh, and I also played with all my bios settings relating to sata and ide. no difference. I haven't tried updating the bios but I just recently purchased this board.

Can anyone help me out here? I've spent days getting everything working on this machine, and this is really frustrating me. If you think you could help me if I gave you any more logs or config files, I'll be glad to post them.

In any case, thanks for readin

---

### Post by handy on 2009-02-19
Out of interest what software are you using to rip, & are you ripping to DVD-5 single layer size DVD format with a VIDEO_TS folder, or are you doing a conversion?

---

### Post by tsmithtree on 2009-02-19
I tried using mplayer to dump to vob file (no conversion) and I tried ripping with dvd::rip as well. same issue with both software. These are just straight rips; no conversion is taking place. It's not really the dvd ripping that's the problem, it's the read speed of the drive. edit: i should also mention that it's still slow when just copying an iso image of the disc. so it's definitely not the ripping software.

other people seem to be getting somewhere around 40mb or so a second from the hdparm -t test, which would be about what I got on windows. however, on ubuntu on my machine i'm getting anywhere from .5 to 3mb per second which is much slower. I don't hear my drive start spinning the disk like it should, so I tried setting the speed with both setcd and hdparm but it didn't seem to have any effect. Keep in mind that I can READ the disc fine, just very slowly.

---

