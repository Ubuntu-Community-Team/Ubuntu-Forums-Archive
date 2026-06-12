---
title: "very very slow hdd"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by Pirate on 2006-12-25
i have been using ubuntu 6.10 on my laptop for a month ,
in the first week all was ok. but now the hdd is extremly slow 
if i write 
sudo hdparm -t /dev/hda1:

/dev/hda1:
 Timing buffered disk reads:    2 MB in 18.84 seconds = 108.68 kB/sec

i dont use any external hdd and i dont use windows or some other OS just auto partitoned by ubuntu 

does anybody know how to fix it??

---

### Post by xyz on 2006-12-26
Have you tried this:
[Enable DMA]("http://doc.gwos.org/index.php/DMA")

---

### Post by Pirate on 2006-12-26
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 117210240, start = 0


dma look already enabled do you have something different?

---

### Post by blink on 2006-12-27
That speed is certainly unreasonably slow.. Can you post the output of "sudo hdparm -i /dev/hda"? It may be that the hard drive access mode is strangely autoconfigured.

---

### Post by Pirate on 2006-12-27
i believed it was so because i used utorrent with wine but now i dont think so,

after all i deceided to install pardus(another distro) its like ubuntu on debian 

and its now fresh installed on my laptop its not so slow like before but not fast enough 

 Timing buffered disk reads:    2 MB in  4.21 seconds = 486.23 kB/sec


/dev/hda:

 Model=IC25N060ATMR04-0, FwRev=MO3OAD4A, SerialNo=MRG30HK3KKD3WH
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7884kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

---

### Post by Magni on 2006-12-28
speed up your hdd with [hdparm]("http://en.wikipedia.org/wiki/Hdparm")
or test some of [this links]("http://www.google.de/search?hl=de&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=Yba&q=hdparm+howto+speed&btnG=Suche&meta=")

have fun

---

### Post by blink on 2006-12-28
Your HD seems modern and udma4 should be about 20x faster than what you're seeing.
I have had slow HD problems with the gui (kde or gnome) running. You might try running 'sudo hdparm -t /dev/hda' when you're in a console (alt-ctl-f1) and logged out of the window manager.

You may also check if your HD has S.M.A.R.T. You can use the program smartctl to run diagnostics on your HD.

Try "sudo smartctl -a /dev/hda" to see the HD status and "sudo smartctl -t long /dev/hda" to run a long (hour) test on the HD.

The final suggestion, would be to check that your IDE chipset on the motherboard is ok. You can browse the output of "dmesg|less" to see if there's some dire warning in their.

---

### Post by Pirate on 2006-12-28
i tried in console like you said it look better but not bir difference 
Timing buffered disk reads = 1.20 Mb/sec 

so i install smartctl and i wrote 

sudo smartctl -a /dev/hda :

i put output as file because its long



i wrote this : smartctl -t long /dev/hda also
and i am waiting now

---

### Post by blink on 2007-01-01
How did the long SMART test go? I looked through your output from the smartctl command and it shows a few low-level drive errors. I think your drive may be beginning to fail. If so, this isn't a linux-specific thing, it's a bad hardware thing. Try/borrow a replacement drive and things may be a bit rosier..

---

