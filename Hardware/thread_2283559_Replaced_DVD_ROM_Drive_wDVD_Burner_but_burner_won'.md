---
title: "Replaced DVD ROM Drive w/DVD Burner but burner won't work"
date: 2015-06-22
forum: Hardware
---

### Post by Larry_Crouse on 2015-06-22
I'm running Ubuntu 14.04 LTS Server and had a DVD Reader in it. I wanted to burn some files so switched out the DVD reader for a DVD burner. the burner will read discs but does not recognize blank media.

sudo lshw  gave me:

*-cdrom
        description: DVD reader
        product: CD-RW    CRX320EE
        vendor: SONY
        physical id: 0.0.0
        bus info: scsi@0:0.0.0
        logical name: /dev/cdrom
        logical name: /dev/sr0
        version: RYK4
        capabilities: removable audio cd-r cd-rw dvd
        configuration: ansiversion=5 status=nodisc

this was taken with a blank DVD in the drive

I'm fairly new to Linux so not sure where to go to fix this. But it looks like some of the settings from the DVD reader are still in place and the settings for the burner haven't been loaded.

I know the burner works because I used it 3 days ago in a windows machine and I can read cd's and dvd's on my server. Brasero Disc Burner software does not find my burner either

---

### Post by Vladlenin5000 on 2015-06-22
Hi and welcome.

Sony CRX320EE reads and writes CDs but only reads DVDs. Not recognizing a blank DVD is the expected behaviour since it ISN'T a DVD burner.

---

### Post by Larry_Crouse on 2015-06-22
many thanks I will try again with another drive that I know for certain is a dvd burner

---

### Post by Vladlenin5000 on 2015-06-22
You're welcome :-)

---

