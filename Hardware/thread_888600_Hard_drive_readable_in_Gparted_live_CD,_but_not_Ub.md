---
title: "Hard drive readable in Gparted live CD, but not Ubuntu 8.04?"
date: 2008-08-13
forum: Hardware
---

### Post by Phreak64 on 2008-08-13
Hi all.  I'm new to the forums, and actually rather new to Ubuntu in general.  I haven't run a Linux distro in a long time, but am looking to set up a Vista/Ubuntu dualboot on the machine that I bought recently.

The problem is that while the Gparted 0.3.7 live CD that I burned and have used can read my hard drive and its partitions just fine.  I have a primary NTFS Vista install partition of about 120GB, a logical NTFS Files partition of ~800GB or so, and a logical 15GB ext3 Ubuntu partition.

Gparted was able to create them perfectly.  The Vista install DVD reads them, and is able to install itself to C: as it's supposed to.  The problem is that the Ubuntu Hardy Heron 8.04 live CD which I downloaded and burned doesn't seem to see any of my partitions at all.  Booting into the Ubuntu live environment and running Gparted 0.3.5 on that machine doesn't see anything, and looking in the /dev folder doesn't seem to turn anything up either.

As such, I cannot install Ubuntu 8.04 like I would really like to do.

:(

My hard drive is a Seagate Barracuda 1TB drive, ST31000340AS.

[http://www.seagate.com/ww/v/index.jsp?vgnextoid=0732f141e7f43110VgnVCM100000f5ee0a0aRCRD](http://www.seagate.com/ww/v/index.jsp?vgnextoid=0732f141e7f43110VgnVCM100000f5ee0a0aRCRD)

It has the jumper removed to remove the 1.5Gb/s restriction, and the BIOS is reading it as an IDE drive (AHCI gives Vista all sorts of problems).

The strange thing is that Gparted 0.3.7 reads it wonderfully.  It's just the Ubuntu install disc that cannot read it, and so it cannot install anything.  Is this due to the outdated Gparted version on the Ubuntu install disc, or maybe something else?  A driver issue, perhaps?  Any help from Linux vets would really do me a bit favor here.

I'm not at my PC now, but I will be tonight.  I just wanted to throw this around.  Please forgive me for not knowing a ton about Linux aside from some basic operating bits.

Thanks!

---

### Post by logos34 on 2008-08-13
That's odd about AHCI giving vista problems--vista is supposed to natively support it (no loading drivers on floppies necessary)...

The gparted on the Hardy 8.04 live cd is vers. 0.3.5 or 0.3.3 I believe...wonder why it's not cooperating.  Have you tried to start up the installation (desktop 'Install' icon)?  Sometimes the Ubiquity installer partitioner can see the partitions fine where Gparted cannot,

---

### Post by Phreak64 on 2008-08-13
Well, a bit of an update.  Instead of waiting for Vista to be completely installed before setting up AHCI mode, I made a floppy with the AHCI drivers on it for Vista to load in the initial config.  So far, it works better, and when AHCI mode is enabled on the drive, Ubuntu can find it!

So, for now, it looks like this is solved.  Strange, though, that Ubuntu 8.04 couldn't detect the drive in IDE mode when Gparted could.  In any case, I think the workaround will hold for now, as long as Vista remains stable enough for the dualbooting.

---

### Post by logos34 on 2008-08-13
that's odd about ubuntu too--it should be able to detect and run the drive configured either way...hmm.

anyway, glad it's all ok now

---

