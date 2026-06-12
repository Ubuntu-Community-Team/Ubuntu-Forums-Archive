---
title: "How do I install two copies of ubuntu on the same hdd?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by c3lica on 2009-04-23
Ok, I want to run Ubuntu Server 99% of the time but some of the time I want to be able to run desktop. 

Really I think the only thing I need to know would be how to partition the drive and if I should install desktop or server first... I would think that it would not matter.

So yeah, how should I partition an 80gb drive?

---

### Post by dabl on 2009-04-23
For 1% of your usage, you're going to install a whole separate OS?

:shock:


Well, OK, make 2 partitions 8GB each for the two OSs, make a swap partition of the best size that your research tells is right for your hardware and hibernation plans, and the rest of that drive (the fourth partition) can be for data.  You can use Gparted or Parted Magic -- Google will tell you where you can download ISO files to make a Live CD if you wish.

---

### Post by PaulReaver on 2009-04-23
The easiest way I could imaging would be to install server first and then install the desktop Second. 

Using the graphical installer would be easier than using the command line to repartition the disk. 

I can't tell you what your patition sizes should be, it depends what your using desktop/server for.

---

### Post by c3lica on 2009-04-23
> **dabl said:**
> For 1% of your usage, you're going to install a whole separate OS?

That number isn't completely accurate... the server will run as a file server most of the time but I plan on using it sometimes to convert cassette tapes and vhs tapes to cd and dvd for my parents but mostly it will be running as a file server. 

Anyways, Thanks for the help. I will give what you guys said a shot. I didn't realize I could repartition with an os installed with our ruining it.

---

