---
title: "Disabling DMA on usb card reader?"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by zi99y on 2005-12-08
I read somewhere that it's dangerous to your flash media to have DMA enabled as it increases the writes to the drive and will shorten the life of the media. I've looked around this forum for more info and can't really find any, my card reader works ok, but it seems to put files in a funny order and there's something I don't quite trust about it.

Since it is governed by the automounter, and not mentioned in /etc/fstab or /etc/hdparm.conf , how can I alter or view the DMA settings for this?

cheers :-\"

---

### Post by mlomker on 2005-12-08
DMA is only on for IDE devices.  If your reader is USB then you won't have to worry about it.

You use **hdparm** to check or set DMA settings on IDE devices.

```

mlomker@mlomkernote:/$ sudo hdparm -v /dev/hda
Password:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 117210240, start = 0

```

---

### Post by zi99y on 2005-12-09
Thanks, I must have got the wrong end of the stick, I'll have a look around to see if I can find that page again. But this has quashed my fears. Ta

---

