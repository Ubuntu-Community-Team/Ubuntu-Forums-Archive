---
title: "can't copy files larger then 32KB from my very old 1997 Hard Drive"
date: 2011-02-06
forum: Hardware
---

### Post by kdogg on 2011-02-06
Hi, 
I want to copy all files I have on my old HD, a caviar 36400 (I think its from around 1997), 
So I hooked it with a USB/IDE cable, booted my laptop[[COLOR=blue][/COLOR]]("http://www.tomshardware.com/forum/266264-32-trying-copy-1997-files-32kb#")with ubuntu (thought it would be more reliable then myvista), and connected it. 

after 5 min, it finally recongized the HD, it is 2.1GB, and it shows the files and folders, 
but when trying to copy any file larger then  32KB, I get some I/O error,
and it creates them only as 32KB files on the destination HD (a WD  1TB external drive). 

is due to different format systems? (maybe the old one is  fat16? i don't know... the new HD is NTFS), if so, is there a solution for this? how can i transfer all the data correctly? 

I don't think the files are corrupted because it does read them correctly,
for example I can see the thumbnails of images that are on the old HD...
maybe I can try to burn the files with a CD?

thanks!

---

### Post by markthekdeguy on 2011-02-08
sounds like the drive is dying or the cable is bad / damaged.
if the drive is bad (my guess) its more than likely bad sectors,
the SMART data may well be unaware of any read/write crc errors
so i suggest a disk check with suitable software

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

has a few utilities on i think, can be trick to find the correct tool.
windows chkdsk may try, or if you have a friend who owns Steve Gibsons 
'Spinrite' from GRC program you'll prob find bad sectors.

USB connected drives are no good really for checking or doing any important disk operations i reckon, often the USB controller doesn't
correctly translate calls from the IDE or SATA hardware reliably or quickly,
and seeing how the disk is exhibiting problems, you need to connect to the motherboard directly. USB translation is just getting in the way.

i doubt the motherboard is incapable of driving it properly, they generally
detect any HD and suitable params when in POST. 

i have seen similar errors on a PC with a old but slightly damaged IDE cable. try another if poss. maybe observe if a blue DMA 80 or older 40 pin
cable is required. it may help if you have a change of cable.

sorry i cant be of much use though.

Good Luck
Mark

---

