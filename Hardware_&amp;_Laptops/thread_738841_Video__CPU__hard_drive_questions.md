---
title: "Video / CPU / hard drive questions"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by raevin on 2008-03-29
I have a few questions here...all related to a system I'm buying soon...

1)  How is 64-bit support now with Linux?  I remember reading a while ago it was rather...shakey...to say the least, so I'm wondering if that's improved (this was about 2 years ago).

2)  Gonna throw this all into one question, 'cause it amounts to the same...will this set up work fine for Linux (not sure how SATA support is, as well as the video card mainly):

Hard drive: Seagate Barracuda 7200.10 250GB Hard Drive - 7200, 8MB Buffer, Serial ATA-300
(TigerDirect link: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3247662&sku=TSD-250AS6](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3247662&sku=TSD-250AS6) )

Video: Radeon X600 SE
(TigerDirect link: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3501648&sku=TC3H-1134](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3501648&sku=TC3H-1134) )

-----------

Yeah, I know the video card isn't anything fancy...but, I'm not wanting to run Beryl or anything like that...so, it fits me well.

---

### Post by sdennie on 2008-03-29
> **raevin said:**
> I have a few questions here...all related to a system I'm buying soon...

1)  How is 64-bit support now with Linux?  I remember reading a while ago it was rather...shakey...to say the least, so I'm wondering if that's improved (this was about 2 years ago).


It's very good.  The only issues you will have running 64bit are that non-opensource things can be a bit dodgy (wifi drivers, adobe flash, etc).  As far as I can tell, the only real reason to go to 64bit is if you need a single application that will saturate 32-bit address space (so, it uses more than 2G of RAM (yes, this is not quite accurate, but, it's the general idea)).  If you are moving to 64bit simply because you have a machine with a ton of RAM, you may be better off building a custom kernel with PAE enabled (that is what myself and co-workers use for our 4GB+ machines).

> 
2)  Gonna throw this  However, you can pre-burn an Ubuntu install CD and literally stick i all into one question, 'cause it amounts to the same...will this set up work fine for Linux (not sure how SATA support is, as well as the video card mainly):

Hard drive: Seagate Barracuda 7200.10 250GB Hard Drive - 7200, 8MB Buffer, Serial ATA-300
(TigerDirect link: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3247662&sku=TSD-250AS6](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3247662&sku=TSD-250AS6) )

Video: Radeon X600 SE
(TigerDirect link: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3501648&sku=TC3H-1134](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3501648&sku=TC3H-1134) )

-----------

Yeah, I know the video card isn't anything fancy...but, I'm not wanting to run Beryl or anything like that...so, it fits me well.

You'll have no problem whatsoever with the disk.  I've never used ATI cards but, from what I've heard, support is getting much better for them (they are releasing specs to the community to write drivers now).  Even if that card is 5 year old technology, you'll likely be able to run Compiz/Beryl better than the majority of nvidia [laptop] users...  ;)

---

### Post by raevin on 2008-03-29
> **vor said:**
> It's very good.  The only issues you will have running 64bit are that non-opensource things can be a bit dodgy (wifi drivers, adobe flash, etc).  As far as I can tell, the only real reason to go to 64bit is if you need a single application that will saturate 32-bit address space (so, it uses more than 2G of RAM (yes, this is not quite accurate, but, it's the general idea)).  If you are moving to 64bit simply because you have a machine with a ton of RAM, you may be better off building a custom kernel with PAE enabled (that is what myself and co-workers use for our 4GB+ machines).

Actually, I'm not even really wanting to go 64-bit, it's just the processor that the motherboard comes with (I'm getting a barebones kit that comes with a motherboard, processor and some memory).  But, if need-be, I'll look into the custom-kernel thing.

> 
You'll have no problem whatsoever with the disk.  I've never used ATI cards but, from what I've heard, support is getting much better for them (they are releasing specs to the community to write drivers now).  Even if that card is 5 year old technology, you'll likely be able to run Compiz/Beryl better than the majority of nvidia [laptop] users...  ;)
Hehe, awesome.  Well, I find a thread on this forum from a few years ago that talked about how to get the video card to work with Ubuntu, so I'm assuming that that's been fixed now. :)

Thanks for the information!!!

---

