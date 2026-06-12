---
title: "Knock-Knock. Who's there? Hard drive failure. (backing up data before the hard drive)"
date: 2008-08-12
forum: Hardware
---

### Post by palian on 2008-08-12
I think my hard drive is dying and was hoping to get some advice as to the best way to get the data off the hard drive before the inevitable occurs.

So I went home for lunch yesterday and started up my computer. But nothing was listed when it got to the part of the boot sequence where the hard drive is recognized. So I rebooted and tried again with then the same results. I rebooted one last time and opened up the case and wiggled the SATA cable. That time it booted but I heard a knocking noise in the hard drive similar to a clock ticking in rhythm and tone. 

My thoughts are I can either buy another internal hard drive to replace the current one (at least temporarily) and move the data to it. Or I could buy an External and use it for storage after I get the data off and either repair or replace the hard drive. But what I mainly curious as to what method of data migration people would use in this situation.

The hard drive that is going bad (as far as I know) is 500gb Seagate that came with a 3 year warranty (this is the second year of use) with 120g - 140g of data on it.  Most of the data is one the Ubuntu partition but there maybe somethings I want to keep from the XP side.

---

### Post by starcannon on 2008-08-12
I'd boot from a LiveCD, plug in an external USB drive, mount your failing drive, copy the /home directory over to the external drive, verify the data is truly and faithfully represented on a separate computer, and then start troubleshooting the Hardware.

Mount the windows partition, find the documents you want and copy them over to the external drive, in a folder named wth, "My_Documents"

Back up the /home directory and your \My Documents(and any other folders where you put stuff) before you do anything else.

---

### Post by tango_ninja on 2008-08-12
This happened to me a couple months ago....my WD hard drive started clicking and Ubuntu was freezing all the time (see old post here for details: [http://ubuntuforums.org/showthread.php?t=710862](http://ubuntuforums.org/showthread.php?t=710862))

Run *dmesg* to check..

I booted from liveCD, plugged in an external HD and spent a **long** time copying my data over. One of the reasons it took so long is because of the bad sectors on the HD. (took hours to copy some larger files).

I did this all through the terminal, recursively:

```
cp -R /path/to/copy_directory/* /path/to/paste_directory/
```

---

### Post by palian on 2008-08-12
I would guess that no one is recommending using image backups at this point?

---

### Post by iamajd on 2008-08-12
I had a hard drive fail on me near the end of last year.  Before it completely disintegrated, I used "dd_rescue if=/dev/sdb of=/dev/sdc" to copy the entire disk image to a new drive.  It was a 250gb hard drive (copied to a 320) and it didn't take *that* long.  Then I used fsck on the new drive.  Everything was completely recovered except for 5 easily replacable files.  I don't remember the exact fsck options I used, but it was a reiserfs partition and had some great recovery options.  Best of luck!

Edit:
In case you are wondering about the differences between dd and dd_rescue, here is a helpful article:
[http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/)

---

### Post by cariboo on 2008-08-12
If you are having a hard time getting the drive to boot, stick it in the freezer for a couple of hours the put it between a couple of ice bags to keep it cold while you are recovering your data.

Jim

---

### Post by hypatia on 2008-08-13
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html) is what you want to use, off a live-cd as others have mentioned. it is a newer implementation of dd_rescue which was mentioned earlier, but much better.

it skips over the bad sectors and gets as much data as it can off the drive before going back and accessing the bad sectors.  it works great.

---

