---
title: "install issues"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by ZizzerZuz on 2009-08-18
system 1:

IBM Xserries 220
2gb Ram
Dual 1.2 ghz procs
2x36gb SCSI drives
1 76gb SCSI drive
standard IDE CD drive

Windows 2000 loads and runs just fine and recognizes PCI Adaptec aha-2930CU SCSI card

Ubuntu loads and boots without the card installed

Open Suse won't load at all

With the PCI SCSI card I get AOPIC erros, then goes into something about busybox and stalls out and drops to a root shell.


System 2
Dell E310
2gb ram
250 gb SATA HD
SATA DVD/RW drive
Everything I try with ubunutu just fails.  The drive reads enough to boot, but it just won't load.  I get the splash page and the choices to install or run without changes but it won't do either.  I've gone through the f1, f2 etc, I've tried to turn of the APIC stuff, I've dropped down to a safe display mode.

Oh ... same boot media as I used to load ubuntu8.04.1 desktop on another PC and worked ... as in reformatted the drive and reloaded to make sure the media works.

What else can I tell any of you that might help?

---

### Post by ZizzerZuz on 2009-08-19
The IBM X serries is now booting and runningubuntu just fine.  The latest updates have run, it's rebooting cleanly and I don't have to boot to recovery mode!  Hurray!!

Trying the SCSI card again now.  Will post results.  

Is there a way to capture the terminal output to another PC?  I've got serial cables, adapters, null modems, etc..  Cables and or standard adapters are not a problem if there's a way to hook it up to capture those messages.  Alternately, I do have a working copy of Windows 2000 running on another partition, is there a way to get to the dmsg and or boot errors from Win200?  

Any suggestions on what I can look at or info I can bring back here that can help make this work?

Shutting down to try the scsi card again now.

---

### Post by ZizzerZuz on 2009-08-19
I have shut down, power cord out
installed SCSI card
booted with external SCSI enclosure with CD-R and multi card reader
Comes up to an error that amounts to no boot media found.
shutdown, power off, turn off SCSI enclosure
boots right up to ubuntu, no SCSI errors
power on the external enclosure and I can't access it also I can't seem to get to the IDE CD Rom drive

I would REALY like to get this SCSI enclosure to work as it has a CD-R and I would like to use it to make back ups etc.  The card reader would be nice, but not needed.

excerpts from sudo dmesg | more :

18.404051] scsi2 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   18.404055]         <Adaptec aic7892 Ultra160 SCSI adapter>
[   18.404057]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   18.404060] 
[   18.404453] aic7xxx 0000:01:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.411307] scsi 2:0:0:0: Direct-Access     IBM-ESXS ST336605LC    !# B245 PQ: 0 ANSI: 3


and I think this is the IDE CD drive

[  756.168868] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  756.168899] sr: Sense Key : Aborted Command [current] [descriptor]
[  756.168914] sr: Add. Sense: No additional sense information


Thoughts?  Ideas?  Suggestions?

---

