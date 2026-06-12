---
title: "cd burning woes"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by mbdayton on 2005-05-01
I've searched through this forum and others pretty throroughly and I haven't figured this one out yet, although I've seen a lot of similar problems.

I'm trying to use cdrecord to burn an iso on a Dell Dimension 8100 running Ubuntu.  when I try to run scanbus I get this:

> Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

Any ideas?

---

### Post by nad on 2005-05-01
You can just right click your iso and choose Write to Disc. Works fine.

Apparently nautilus transparently maps to your ide device if it even uses cdrecord. I find this a little awkward also as I am just so use to the command line. Been meaning to figure it out.

---

### Post by mbdayton on 2005-05-01
I keep getting an error message telling me to insert a blank disc.  It ain't cause there's not a disk in there either.

---

### Post by nad on 2005-05-01
Hmmm...

This is begining to sound like one of those hal | dbus | gvm problems.

---

### Post by mbdayton on 2005-05-02
You've piqued my interest.  What the heck is hal | dbus | gvm?

---

### Post by nad on 2005-05-02
Hal is the Hardware Abstraction Layer, dbus is a messaging system (much like that used in clusters) and the all powerful, all knowing Gnome Volume Manager which is supposed to assimilate this. Until the devs get all the bugs worked out it's going to be like that other os for a while, What's Going to Work Today!

---

### Post by mbdayton on 2005-05-03
any ideas about how I can at leat burn an iso?

---

### Post by LongTooth on 2005-05-03
I burn ISO very easily using Gnomebaker. Odd thing though, just yesterday I tried my hand at copying an audio CD. No go. Something I'll have to look into. But to get back to ISO burning; I've been able to burn ISOs with a problem using Gnomebaker.

If you're using Hoary it comes with it. Look in Applications> Accessories > Gnomebaker.

---

### Post by christooss on 2005-05-03
Check this page. You have to enable burn proof and other options

[URL=http://ubuntuforums.org/showthread.php?t=12133&highlight=blank+disc] 	
Nautilus CD Burner doesn't recognise blank disks [/URL]

---

### Post by christooss on 2005-05-03
[QUOTE=LongTooth]I burn ISO very easily using Gnomebaker. Odd thing though, just yesterday I tried my hand at copying an audio CD. No go. Something I'll have to look into. But to get back to ISO burning; I've been able to burn ISOs with a problem using Gnomebaker.

If you're using Hoary it comes with it. Look in Applications> Accessories > Gnomebaker.[/QUOTE]
 You have to install gnome baker. It doesn't come with Hoary

sudo apt-get install gnomebaker

---

### Post by nad on 2005-05-03
Yep. It looks to be a firmware issue between your writer and gnome/nautilus. Try the suggestions in post#9 and/or try a dedicated burning app per the other poster.

As far as burning from cli, set it up the old way with kernel ide-scsi support, add the scsi driver to your modules list and adjust permissions (whew). This would likely break something else though.

---

### Post by mbdayton on 2005-05-03
thanks for all the great ideas.  I'm pretty sure I've already set burnproof, but not overburn and debug.  I'll also try gnomebaker.

> As far as burning from cli, set it up the old way with kernel ide-scsi support, add the scsi driver to your modules list and adjust permissions (whew). This would likely break something else though.

I hope to someday know what this means.  But hey, its just another distro. Might as well start messing around with kernel.

---

### Post by mbdayton on 2005-05-04
everything is working great.  Thanks again!

---

### Post by ducko on 2005-05-04
Hi!

So you finally got it working? What did you do? I have the same kind of problem when copying audio CD: same error message etc. That happens when copying to disk has ended and GnomeBaker should start writing to blank CD.

-ducko

---

### Post by Jarz Corp on 2005-05-04
I would say don't spend to much time on baker, it is hysterical with disc limits. It thinks that a 700mb disc is 700mb and not an inch more.

I am abusing graveman right now, and for me on my system that has been the most stable solution, gui wise that is. If we dropped burning discs through a gui we wouldn't have half the problems, and then we could spend all our time on cdrecord-mkisofs commandline options.

---

### Post by IcemanV9 on 2005-05-04
Oy! I cannot burn ISO to a disc or even blank CDRW disc. I have tried all suggestions in this thread (and via Google). NOTHING works! I also have installed/tried many apps (K3B, GnomeBaker, XCDRoast, Nautilus). NOTHING still. I am going NUTS for trying to resolve this problem! ](*,) Please help me.

I am using Hoary 5.04 (installed last week). It ROCKS, but CD issue needs to be resolved before I can brag to my friends & family.

CD drive: QSI CD-RW/DVD-ROM SBW-241
Laptop model: hp pavilion ze5185

Thanks.

---

### Post by Jarz Corp on 2005-05-04
Well lets see some errors then, give us a screendump or even better a logfile.

---

### Post by mbdayton on 2005-05-04
Ducko,

checking burnproof, overburn and debug in the nautilus burner configuration turned out to be the answer.  Although I'd still prefer to do it all with cdrecord.

---

### Post by LongTooth on 2005-05-05
mbdayton, a little more clarity if you would please. You see while I have no problem burning ISOs to a CD with Gnombaker, I can't copy an audio CD. So I'm thinking your research will help. But you've left me in the dark. Explain in detail please. Thanks.

---

### Post by IcemanV9 on 2005-05-05
CD drive: QSI CD-RW/DVD-ROM SBW-241
Laptop model: hp pavilion ze5185

UPDATE: I found the (temporary) solution from the bugzilla (bug #7382). "cdrecord -immed" (via CLI) seems to be working with 'QSI' cd drive. I was able to blank a CDRW disc & burn ISO. Also, blanking a CDRW disc option is STILL no go from all apps (K3B, GnomeBaker, XCDRoast, Nautilus). Hopefully, it will be fixed in the near future.

---

