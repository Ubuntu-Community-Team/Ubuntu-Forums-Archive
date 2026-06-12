---
title: "Xsane can't find Artec AM12S scanner"
date: 2009-04-16
forum: Hardware
---

### Post by dhochmuth on 2009-04-16
I'm using 8.10.  Okay  Here's the results from sudo sane-find-scanner

david@david-desktop:~$ sudo sane-find-scanner -v
This is sane-find-scanner from sane-backends 1.0.19

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
checking /dev/sg0... open ok
found SCSI scanner "ARTEC AM12S 1.06" at /dev/sg0
checking /dev/sg1... failed to open (Invalid argument)
etc.

According to sane-project documentation, ([http://www.sane-project.org/sane-backends.html](http://www.sane-project.org/sane-backends.html)) the AM12S backend is unmaintained but status is complete/all modes working.  Whether I log on as david or as root (and get a big warning) all I get when I run xsane is "no devices available".  For completeness here's my results from "sudo lsmod | grep dmx" (I have no idea what that returned info about the scsi card means. It is a Domex 3191D pci card.  I saw the command on another thread.)

david@david-desktop:~$ sudo lsmod | grep dmx
[sudo] password for david: 
dmx3191d               19328  0 
scsi_transport_spi     30464  1 dmx3191d
scsi_mod              155212  7 sbp2,sr_mod,sd_mod,sg,dmx3191d,scsi_transport_spi,libata

I tried adding david and root to the "scanner" group in user settings of the System>Administration>Users and Groups, but that didn't help.

The sane-find scanner also gave this instruction

  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

Here are those results:

david@david-desktop:~$ sudo scanimage -L
[sudo] password for david: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

Please help.  I'm a brand new user so it needs to be specific and complete instructions without lots of jargon/acronyms/implied steps.

Thanks

Dave

---

### Post by dhochmuth on 2009-04-20
Well I finally figured out my problem.  I suspected it was a permission issue and followed the instructions here:

[http://www.soslug.org/astra1200s](http://www.soslug.org/astra1200s)

Still no go.  After much searching, I took a look at the etc/sane.d/artec.conf file.  The first line was 

SCSI ULTIMA

which I suspect is because ARTEC was made by ULTIMA.  On a hunch, I changed ULTIMA to ARTEC and Presto! Now it works.:D

So if anyone else is having trouble with an Artec scanner, check the configuration file.

Dave

---

