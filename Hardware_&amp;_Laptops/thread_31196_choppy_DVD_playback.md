---
title: "choppy DVD playback"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by marks_linux on 2005-05-02
I'm having problems with DVD playback. Visuals momentarily pause and sound becomes out of sync when using totem. I setup DVD playback as per the 5.04 getting started guide.

Running 32bit 2.6.10-5-k7
 kernel on AMD64 3200+ ATI radeon graphics with fglrx up and running (around 2000fps in glxgears). Playback from harddrive is good so looks like DVD drive.

Heres the current info I think? is important:
/dev/hda:
 Timing buffered disk reads:    6 MB in  3.06 seconds =   1.96 MB/sec
markw@markhome:~/dist$ sudo hdparm -T /dev/hda

/dev/hda:
 Timing cached reads:   2500 MB in  2.00 seconds = 1248.32 MB/sec
markw@markhome:~/dist$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=_NEC DVD_RW ND-2500A, FwRev=1.06, SerialNo=
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode

Anone any ideas?

Cheers
M

---

### Post by Professor X on 2005-05-02
Enter the command ```
sudo hdparm -d1 /dev/hda
``` 
The [restricted formats wiki](http://www.ubuntulinux.org/wiki/RestrictedFormats) tells you how to enable this permantly for your dvd drive.

---

### Post by alastair on 2005-05-02
FYI, I have a thinkpad with an ATI graphics card.

I had to install the ATI fglrx driver recently to run a specific app. but discovered that DVD playback with it was very INFERIOR (vertical refresh rate issues) than the open source "ati" driver.

Not sure if this is related to your issue, but worth a thought.

---

### Post by marks_linux on 2005-05-03
I found this thread and am going to work through it and see if I can get things going!

[http://ubuntuforums.org/archive/index.php/t-24046.html](http://ubuntuforums.org/archive/index.php/t-24046.html)

Cheers
M

---

