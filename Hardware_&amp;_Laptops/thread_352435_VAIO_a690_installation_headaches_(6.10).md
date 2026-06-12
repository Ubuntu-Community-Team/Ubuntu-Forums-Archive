---
title: "VAIO a690 installation headaches (6.10)"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by abstrakt on 2007-02-03
**SOLVED!** (see edit 2)

Hi everyone,

I've done a lot of digging on this problem both by searching the Ubuntu forums and asking Dr. Google, but I'm not having a lot of luck with a solution.  Here's some of the details about my situation:

(please excuse my long winded typing, I always figure too much info is better than too little)

I have a Sony VAIO vgn-a690 laptop.  I have attempted to use both the CD iso and the DVD iso of Edgy 6.10 to install.  I've also read about the woes of the included DVD-RW drive, so I've attempted installing with various versions of the firmware, including most recently the latest release from Lite-ON (even though it's badged as a sony drive, it's actually something else).  The built in hard disk is SATA, though I don't know the SATA chipset that it uses on the motherboard.

So here's the deal.. 

The CD boots, no problem, but it takes a long, LONG time to get past the initial splash screen with the scrolling orange bar.  The bar itself moves very, very slowly back and forth while it's scanning, or doing whatever exactly it does at this point.  [Odd note here, if I move an attached USB mouse around during this stage, the bar moves more quickly, but slows down again when I stop with the mouse.]

Eventually, usually that is, it'll continue on to a black screen with nothing at all.  It will sit here, again, for a very long time.  At some point in the not-too-distant future, if all goes well, I'll boot into the live cd desktop environment.  I have a number of issues here, including lack of wi-fi support, but that's not the intention of this post so ignore the previous sentence :p

The big problem is when I go to install the OS to the hard disk.

Originally, I would get to the final stage and no hard drive was detected at all.  Somehow, perhaps by divine intervention or sunspots or alien abduction, I'm really not clear exactly, the most recent time I installed led me to a fully detected SATA drive, but again the detection stage took a long time.  [It should be mentioned, when I say long time, we're talking 15-45 minutes for some stages of this process].  When I finally told it to partition my empty space (which I had pre-arranged using partition magic) the partition process fails, and I'm not able to make it any further.

ARGH!

Ok, so as I am posting this message, I have pre-partitioned the empty space with an extended 13gb ext3 partition and a 2gb swap partition, but it remains to be seen if anything will improve.

Any advice???  What the heck is happening here?  Is it a matter of pre-installing SATA drivers perhaps?  Is my DVD drive bunk?  Does a race of superintelligent pandimensional beings really control the fate of the earth?  Inquiring minds need to know!

Thanks for reading.

[edit: ok so I booted into the live dvd again, this time with the pre-partitioned drive as previously mentioned, and this time my only option during step 5 of installation is "manually edit partition table."  When I move to step 6, the page is blank with the message at the bottom "No devices detected."]

[edit2: after more searching, I found this link: [http://www.ubuntuforums.org/showthread.php?t=331572&highlight=hangs+on+mounting+root+file+system](http://www.ubuntuforums.org/showthread.php?t=331572&highlight=hangs+on+mounting+root+file+system).  One piece of advice was to hit F6 during install, and add "irqpoll" to the boot line.  It dramatically sped up the installation process, and let me access my hard drive during the partitioning phase!]

---

