---
title: "Problem with DVD/CD burner on Sony laptop"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by Elf on horseback on 2007-07-15
Like it says I am having a problem with my DVD/CD burner drive.  Its in a Sony FS980.  The problem is I went to burn a ISO to CD today and it said insert blank media, even tho i tried 2 CDs and a DVD same thing.  I did use the burner a few times back when I had Windows and I ran the LiveCD a few times.  So I know the read part is ok.  looking over the forum, was not really a help as to my issue.  Any idea what I should do next?

---

### Post by Elf on horseback on 2007-07-15
I ran wodim --devices and I got
```
Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (1 found) :
----------------------------------------------------------------------
0    dev='/dev/sr0'   rwrw-- :  'QSI'  'DVD+-RW SDW-085'
----------------------------------------------------------------------

```

---

### Post by ramjet_1953 on 2007-07-15
What package are you using to burn your iso?

I have found both k3b and GnomeBaker work well.

Regards,
Roger :cool:

---

### Post by Elf on horseback on 2007-07-15
Been using the CD/DVD Creator that comes with Ubuntu.  Is that junky compared to the other ones you said?

---

### Post by ramjet_1953 on 2007-07-16
No, I wouldn't say that, but both k3b and GnomeBaker offer more featues and are easily configured.

I'm not sure about GnomeBaker, as I don't use it myself, but k3b automatically allocates you read and write privileges, as part of the config.

If you do decide to use k3b, it is a KDE application and a few extra packages will be dowloaded, to satisfy dependencies.

Also, when running it under GNOME, it can take a few seconds to start-up as it also needs to load-up these dependencies.

Regards,
Roger :cool:

---

### Post by babysteps on 2007-07-16
> **Elf on horseback said:**
> Been using the CD/DVD Creator that comes with Ubuntu.  Is that junky compared to the other ones you said?

I'm fairly new to Ubuntu and so far have found that I was better able to create a ISO image with the CD/DVD creator than with K3b.  

Also, when I first tried to use my external Sony DVD burner (I didn't have it when I installed Ubuntu, and so had to learn to get it recognized by the system) it complained about the DVD-R blank discs I put in, saying it wants blanks.   I just about gave up and unplugged it from the computer.  I used it with a different machine, also one with Ubuntu on it, but newer verison, and it worked fine.  So this time I plug it back to the first Ubuntu computer, turn on the Sony burner first, and then booted up the computer.  And it was all well again.  

I know this is not one of those high tech experience, but I have found in many instances that I have been too quick to chase the problem when the solution is simpler than expected.

P.S. When the burner wasn't working, the device manager showed that it couldn't write to DVD, nor RW...etc,  had I not seen it listed with all its capabilities except for DVD-RAM before, I would have thought that the burner was no good. So I think sometimes it doesn't pay to try to fix the conditions that are only reflections of a temporary problem at the moment.  The device manager showed it correctly when it worked.

---

### Post by Elf on horseback on 2007-07-16
yah, K3B fixed my problem.  another question is Babysteps talked about a device manager, in my wanderings in Ubuntu I have not seen it.  Little direction, please?

---

### Post by babysteps on 2007-07-16
> **Elf on horseback said:**
> yah, K3B fixed my problem.  another question is Babysteps talked about a device manager, in my wanderings in Ubuntu I have not seen it.  Little direction, please?

In ubuntu 5.10 and 6.06 it's under System - Administration - Device Manager. It shows pretty detailed info about everything that is in, or plugged into your computer. 

In 7.04 it might be called something else: "info center" or something like that.  In any case I don't think you can changed anything in there, it's just a pretty detailed account of what you have at the time.

---

