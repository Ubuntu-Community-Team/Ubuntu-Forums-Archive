---
title: "Any detailed instructions for installing SCSI driver?"
date: 2020-05-17
forum: Hardware
---

### Post by Anaxagore on 2020-05-17
Hi,

I'm using Ubuntu 18.04 (not yet upgraded to 20.04) and have a SCSI card so I can connect to my old A3 scanner that VueScan does support (dual booting with Win10... used to drive the scanner using WinXP mode and the original manufacturer's driver on W7 but WinXP mode isn't part of the W10 license anymore... hence my wanting to try on Ubuntu). It's been quite some time I've been using Ubuntu, but usually without fiddling too much with deep system options, so consider me a newbie there. The card is properly detected when running lspci:

SCSI storage controller: Adaptec AHA-3960D / AIC-7899A U160/m (rev 01)
SCSI storage controller: Adaptec AHA-3960D / AIC-7899A U160/m (rev 01)

so I'd like to try and see if I could have the ahc driver loaded and access that scanner on Ubuntu.

Googling does not help much (a few links, one mentioning the driver, the others defining some terms mentioned in that driver page but that seem to apply to BSD systems rather than Ubuntu 18.04: [http://manpages.ubuntu.com/manpages/bionic/man4/ahc.4freebsd.html](http://manpages.ubuntu.com/manpages/bionic/man4/ahc.4freebsd.html) , [http://manpages.ubuntu.com/manpages/focal/en/man5/loader.conf.5.html](http://manpages.ubuntu.com/manpages/focal/en/man5/loader.conf.5.html) , [http://manpages.ubuntu.com/manpages/bionic/man5/freebsd-config.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/freebsd-config.5.html); I still cannot make sense out of them. Is there even a loader.conf in 18.04?).

Is there a sort of wiki with a detailed procedure showing how to have that driver loaded in Ubuntu 18.04, that is:
- detailed steps on which files to update for the driver to be loaded, AND
- detailed steps on how to recover a working system (i.e. which files to backup before the installation and how to restore them) if the driver does cause a conflict that prevents Ubuntu from booting properly?

Thanks all for the help!

---

### Post by CelticWarrior on 2020-05-17
Have you tested already and didn't work or are anticipating potential problems about drivers?

SCSI adapters are usually supported and yours is since 2007 (probably). So, just connecting the scanner and installing VueScan should be enough, I think, if VueScan actually supports it.

---

### Post by Anaxagore on 2020-05-18
I had not but it seems you are perfectly right. I just tested this morning with an old PCMCIA card reader (Minolta CD-10) and although the card itself (probably defective) did not get auto-mounted, it did appear as /dev/sdc, so I suppose that there is no need to install a scsi driver. Thanks a lot for that suggestion!

I would suggest one thing: on the help page I linked earlier (first of the links), it would be good to mention exactly what you said (especially when 16.04/18.04/19.10/20.04, the versions mentioned at the page top, are all posterior to 2007); that is, above "To compile this driver into the kernel, place the following lines in your kernel configuration file", have a big statement saying that the instructions below only apply to early versions (up to XXX) and not current ones.

---

