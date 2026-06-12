---
title: "Intel X6800"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by dr_pressure on 2007-09-25
Hey folks...

I'm building a new rig... I've already got the processor, it's a Intel X6800 (aka Core 2 Duo Conroe XE).

I'm having trouble selecting a mainboard. It's quite important to me that whatever I buy works with Ubuntu.

I was wondering if those people who are already using the X6800 could tell me what mainboard they're using and if they've had any problems with it.

Much appreciated,
Pressure

---

### Post by dabl on 2007-09-25
Yep.  I went with the D975XBXLKR Intel motherboard ( I think there's a more recent model number).  I figured it would be tough enough to learn Linux without debugging motherboard/BIOS compatibility issues.

I built my rig almost a year ago.  I had a windows partition on it for quite awhile, and I used Intel's utilities to overclock the CPU to 3.3GHz.  It's been running that way ever since, even though there's no Windows partition on the system any more.  Guess if I ever want to slow it down, I'll have to reinstall Windows (that ain't gonna happen ....).

Tip:  Throw away the Intel heatsink/fan that comes with the X6800, and buy an Artic Cooler or Thermaltake or something like that, and be diligent about your heatsink installation.  I managed to bend one of the plastic legs on my first attempt, and decided that the key is to disregard the instruction to put the motherboard in the case first, and then install the heatsink.  You really need the motherboard out on the bench, so you can see the backside and make sure the heatsink legs come through the holes correctly, then install the whole assembly into the case.
, 
:)


EDIT:  BTW, there is a PCI bus error message at the beginning of every boot, regarding some memory address allocation thing.  It's a non-error -- apparently the Linux kernel engineers think it's an Intel problem, and the Intel engineers think it's a Linux kernel problem, so nobody is fixing it, and it doesn't actually affect anything anyway.  ;-)

---

### Post by dr_pressure on 2007-09-26
Cool. Thanks for the heads up on that PCI error.

After posting this yesterday, I went and spent about 4 hours comparing different motherboards... I ended up deciding on the Intel Desktop Board D975XBX (aka Bad Axe).

That's obviously the same as what you've got although my one is the BOX/BLKD975XBXLKR.


Awesome that it works w/ Ubuntu -- and also good that it overclocks, although I'm not planning to overclock at all.

I definitely agree about not putting the mobo in the case before installing the cpu and heatsink :)

Cheers,
-Pressure

---

### Post by dabl on 2007-09-26
Yep, that's the same mobo as I have.

OK, here's a little more unsolicited information for you:

Here's my CPU cooler: [http://www.newegg.com/Product/Product.aspx?Item=N82E16835186134](http://www.newegg.com/Product/Product.aspx?Item=N82E16835186134)

Here's my PSU (don't go cheap on this -- I burnt up the first one which was "only" 500W!): [http://www.newegg.com/Product/Product.aspx?Item=N82E16817371001](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371001)

Here's my RAM: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820146034](http://www.newegg.com/Product/Product.aspx?Item=N82E16820146034)

I don't see the Antec P180B case any more -- it's a monster, but I really like it (I have 5 hard drives, a floppy, and a CD/DVD drive in it).

Put an Nvidia 8600 or 8800 in it and you should be good to go.  :)


p.s. Looks like a good idea to steer clear of the Lightscribe DVD/CD drives.  Mine is an Asus and works great.

p.p.s.  You'll also get a pre-boot BIOS message from the Silicon Graphics RAID controller -- just ignore that too.

---

### Post by dr_pressure on 2007-09-26
So I've been doing a little more research, and I'm going to shoot for the "Bad Axe 2", which appears to be almost identical to what you have but a newer version (D975XBX2).

I've been thinking about heat sink fans a lot lately... I was initially planning to stick with the stock Intel HSF, but basically everybody I've talked to is recommending against that.


I've checked out the Arctic Cooler Freezer 7, and it looks cool, but on the site ([http://www.arctic-cooling.com/cpu2.php?idx=34&data=3&disc=](http://www.arctic-cooling.com/cpu2.php?idx=34&data=3&disc=)) they don't explicitly say it's compatible with the Conroe XE.

Even on newegg it says it's compatible with all Intel Core 2 Duo, Core 2 Extreme Quad -- doesn't mention Core 2 Extreme Duo...



Also the Scythe Infinity seems to be pretty popular -- they do explicitly mention the Conroe XE which makes me somewhat more comfortable about buying it. Not sure if I need it though.

Basically what I'm after is something that will preserve the life of my CPU... I'm not into overclocking or anything like that. But I would like this CPU to have a very long life. I'm planning to keep this machine even after it's long obsolete. For example, I used to run a PII server until it was hit by lightning last year. :)

So what do you recommend... would stock HSF be okay for this?

---

