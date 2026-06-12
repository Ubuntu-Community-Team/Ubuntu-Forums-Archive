---
title: "HD not detected"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by svachs00 on 2006-01-05
Hello, I tried to install Ubuntu 5.10 on HP NetServer LH4 with 8 SCSI hard disks and HP NetRaid MegaRAID and encountered nothing but failure. The install process report no physical disk(s). I disabled HP NetRaid in BIOS and everything is OK,but surely this is  not the way I would like to go. I tried Dapper Drake Flight CD 2 and the install process asked me to put the driver diskette in floppy (I downloaded one from HP website,but this was not the right driver diskette the install process want me to have). I tried OpenSUSE and everything run nicely,but I don't like this distro. There are people who run this system with pleasure - with Fedora or RedHat or SuSE. :-( But I'm looking for someone who can resuscitate HP NetRaid MegaRAID with Ubuntu (or other Debian's).

Sorry about my english, I'm not native english speaker.

Standa.

---

### Post by barratt_sab on 2006-01-31
Hello Standa

First off, I'm no expert - I can only pass on what I discovered yesterday trying to get Linux (of any variety) onto an HP LH4.  I tried Ubuntu (both 5.10 and 5.04), Debian (Sarge), Fedora and Suse.  By the afternoon, I'd got Suse installed (which isn't the distro I wanted, but it's better than nothing (or windoze!)).  Having got Suse on, I then tried a live boot off a 5.10 (i386) CD, which worked (and recognised the disk arrays).

My machine is an LH4 with 2xPII Xeon 450 and 1gig memory and 2 RAID arrays.  The machine has (i) the original on-board NetRaid 1 card; and (ii) a new(er) NetRaid 3 card.  It has one HP standard intel 557 network adaptor.

In the process, I discovered

1.  I have to use the boot options "noapic nolapic" on any distro (try hitting F1 when you get the "boot:" prompt for boot options).  If I don't do this, the install finds two different eth adaptors (even though there's only one in the box!), neither of which work.

2.  The only way I could get the raid arrays to be recognised was to (a) disable the NetRaid 1 card in F2 setup; (b) connect the arrays to the NewRaid 3 card; (c) set up the arrays through the Crtl-M setup; and (d) in that setup set the emulation to "Mass storage" rather than "I2O".

If I do this, I end up with a working system.  There are several long posts on the forum on this topic (try searching for "megaraid" or "netraid" or "I2O") and you could take a look at these too.

If you just have the onboard NetRaid controller, I don't know if these steps will help.  I was lucky - I bought the machine on ebay and it came with an extra card already in it.

I will re-post with anything more that I find today - good luck

Stephen

---

### Post by barratt_sab on 2006-01-31
Well, this morning I tried an Ubuntu 5.10 install from the same disk set as the live version that ran last night, at it stalled (twice).  I tried a debian install and it couldn't see the drives at all.  So, I'm back to Suse 9.3, I guess.  It's not what I want (which is Ubuntu), but if it's all I can get, I'll take it.  Is there anyone out there who knows how to make an LH4 with a NetRaid controller take an Ubuntu install (and can explain it to a non-expert)?

---

### Post by Blade Freak on 2006-02-02
I have the same exact problem
Ubuntu does not find any disk even do they are configured with the NetRAID configure utility and detected when the computer boots.
I guess this is a driver problem since Fedora sees the controller and with Fedora i am able to install a FS and install Linux

Thanks for looking guys

---

