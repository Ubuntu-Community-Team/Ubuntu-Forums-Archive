---
title: "How long should the partitioner take?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by schwim on 2009-10-15
Hi there everyone,

I'm attempting to install Ubu on a computer and chose to install alongside a current Vista install and after fuddling a bit, managed to find the slider to resize the partition(250gb drive and roughly cut it into two equal partitions).  I chose ok, and it stated that it needed to resize the partition before continuing and I chose OK again.  A popup status window came up titled "Please wait" and says "Resizing partion" with a 0~~>100% status bar.  For the last hour, disk activity has been constant and the status bar has remained at 0%

Before I allow it to run all night, I was wondering if someone could tell me if it's normal to have the drive activity go for hours with no status bar change?  I remember a linux install a while ago where it ran for hours because the partitioner was unable to resize the partition properly due to the drive's size, IIRC.  I ended up having to run a dedicated partitioner and resize the partitions in chunks to get a sizable partition.  Is this what I need to do again?

Thanks in advance for any insight you can provide.
json

---

### Post by tuxxy on 2009-10-15
If you are resizing a large partition this could take a while yes much longer than an hour is possible

---

### Post by schwim on 2009-10-15
Thank you very much for your reply Tuxxy.  I guess what I was wondering is this:  Is it normal to show no progress during this time, or should I see something change on the progress bar?

thanks,
json

---

### Post by schwim on 2009-10-15
Well, I guess I've answered my own question. The partitioner errored out and aborted the resize.

thanks,
json

---

### Post by Bartender on 2009-10-15
Have you tried the usual stuff?  Defrag vista a few times, then use th evista partitioner tool (somewhere in Disk Mgmt i believe) to resize vista?

See if you can get vista to shrink itself, then, depending on results, try installing Ubuntu to the freed space.

---

### Post by raymondh on 2009-10-15
> **schwim said:**
> Well, I guess I've answered my own question. The partitioner errored out and aborted the resize.

thanks,
json

Hi Schwim,

Kindly defrag windows before installing Ubuntu.  A fragmented windows partition (of which you are taking space from) can cause trouble during the Ubuntu install.

Kindly try a live session (TRY UBUNTU WITHOUT CHANGES).  It's a good clue of things to come.

Kindly check the CD for defects (one of the options) and MD5.

Regards,

EDIT : Bartender types faster :) LOL

---

### Post by rob2uk on 2009-10-15
Use this guide to resize your Vista partition from inside Windows:

[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista")

Then install Ubu to the free space.

As always, make sure you have a current backup before you do *anything*

---

### Post by schwim on 2009-10-16
Thanks to everyone's assistance, I managed to do it via the Vista resize function and installing into free space.  Thanks to all for your help!

json

---

