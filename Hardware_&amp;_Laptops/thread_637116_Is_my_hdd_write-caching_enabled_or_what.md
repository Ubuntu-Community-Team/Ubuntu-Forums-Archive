---
title: "Is my hdd write-caching enabled or what?"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by logos34 on 2007-12-10
I just noticed something odd while helping another poster with hard disk tuning.  I decided to make a small adjustment to hdparm.  I just installed ubuntu studio x64 and I changed multiple sector io from the default (off) to '16' to speed things up a bit.  I also noted that write caching is disabled, which is the way I want it (I read ext3 fs journaling has issues with it, and anyway I don't notice any performance improvement when it's on).  So I uncommented the middle box below from /etc/hdparm.conf.  Upon reboot multcount was changed correctly but write caching appears to be enabled?  (Also power mgmt read '255' before and after the change reads 'unknown setting.'  (this has occurred before when I've changed the setting of that feature.  But this time I didn't touch it).

Here's the default line:
> 
# -W Disable/enable the IDE drive's write-caching feature
[COLOR="Blue"]#write_cache = off[/COLOR]

I uncommented the following stanza:
> /dev/hda {
	mult_sect_io = 16
	[COLOR="Blue"]write_cache = off[/COLOR]
	dma = on
}




Yet this is what shows up after reboot:

$ sudo hdparm -i -v /dev/hda
> /dev/hda:
[COLOR="Blue"] multcount     = 16 (on)[/COLOR]
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
[COLOR="Blue"] using_dma     =  1 (on)[/COLOR]
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 65535/16/63, sectors = 240121728, start = 0

 Model=Maxtor 6L120P0, FwRev=BAJ41G20, SerialNo=L31TK1LG
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, [COLOR="Blue"]MultSect=16[/COLOR]
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=240121728
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: [COLOR="DarkOrange"]unknown setting[/COLOR] [COLOR="Red"]WriteCache=enabled[/COLOR]
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

Does the 'WriteCache=enabled' merely mean the drive has that particular feature or is it enabled despite the .conf file??

---

### Post by logos34 on 2007-12-10
bump

---

