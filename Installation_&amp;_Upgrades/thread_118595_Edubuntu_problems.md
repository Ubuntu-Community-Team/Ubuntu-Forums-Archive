---
title: "Edubuntu problems"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by ozarkcanoer on 2006-01-17
Yesterday I downloaded and burned **Edubuntu**.  I then took a PC with **Win98**, after having done a defrag and installed Edubuntu as a workstation.  I've got a couple issues.

**1)**I wanted to keep my Win98 partition but it isn't appearing on the Edubuntu boot menu, just three Edubuntu options.  I booted with a Knoppix CD and it showed the Edubuntu partition as a hard disk and what I think is the Windows partition but it wouldn't let me access it.  I looked at the grub menu file and there was no entry for Windows so I added one, maybe incorrectly and then did a upgrade-grub which appeared to run.  I tried booting with the Edubuntu CD but didn't see any partitioning option that would let me redefine the partitions...is there one?  Could I do this with a regular Ubuntu install CD?

Is there anyway to get the Windows partition so it would be accessible at the boot menu? I'd thought about using a win98 boot floppy to put back the MBR and then use the regular Ubuntu CD to put back Grub and hopefully have it create the boot menu list correctly.  Would that work?

**2)**I'm only getting a 640x480 resolution with Edubuntu.  Is this correct?  There wasn't any choice at installation about what resolution(s) I wanted.  Can I get a higher resolution by modifying something in Xwindows somewhere?

 thanks,
Larry

---

### Post by kaamos on 2006-01-17
2) try this command in a terminal
```
sudo dpkg-reconfigure xserver-xorg
```
Select the vesa driver to see if that could work. But installing the correct drivers  for your card (nvidia, ati-fglrx..) will probably be a good idea eventually.

---

