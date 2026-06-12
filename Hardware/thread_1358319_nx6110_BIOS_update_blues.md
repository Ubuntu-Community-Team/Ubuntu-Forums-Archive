---
title: "nx6110 BIOS update blues"
date: 2009-12-18
forum: Hardware
---

### Post by photre on 2009-12-18
Hi,first post here...

working on a friend's 2005 HP nx6110 (Celeron 1.50GHz) upgrade from XP to Ubuntu 9.10
Getting "random" crashes and boot failures with memory paging error messages, that I can't seem to find now in the logs. Sorry.

As others seem to have no major problems with their slightly newer nx6110 machines and 9.10, I casually thought I would start with a BIOS upgrade. 

And there's the problem...

HP only supply windows executable files for BIOS upgrades.

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=449877&prodNameId=449878&swEnvOID=1093&swLang=8&taskId=135&swItem=ob-74571-1&mode=3](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=449877&prodNameId=449878&swEnvOID=1093&swLang=8&taskId=135&swItem=ob-74571-1&mode=3)

I can make a my USB memory stick bootable into FreeDOS - thanks for the existing forum posts on that - but I still need the updater that executes under FreeDOS.  To get it, according to HP, I would need to run their windows exe file that creates a FreeDOS floppy.  Then I could copy the required files from there, put them on the stick and all would be fine. Great, if I had windows and a floppy... but I don't and I don't know who does... noone I know seems to have a working floppy drive and media.

Possibility two seems to be to install windows on the laptop, run their other exe file to update direct from windows (how does that work?), and then delete windows and put Ubuntu back.  Got to be a better way.

So, thanks for reading through.

Can anyone give me the F.16 FreeDOS BIOS updater file and data, please?
Or does anyone think this is all a silly idea/unnecessary/probably won't solve the problem anyway/ has a much better idea/can point out the obvious that I likely overlooked?

Thanks in advance !

---

### Post by IcarusR on 2009-12-19
Could be faulty memory have you tried running 'memtest' from the grub menu ?

---

### Post by photre on 2009-12-21
Thanks, yes I did try memtest and it passed.
I will try dropping back to 9.04 and see how things go.

---

### Post by photre on 2010-01-08
BIOS update to F.14 solved all issues.:D

I never found an intelligent way to do it, so I did it the annoying way... installed XP, ran HP's BIOS update utility, reinstalled Ubuntu.

---

