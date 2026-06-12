---
title: "Help Writing to CD-RWs"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by BitTorrentBuddha on 2006-05-17
Hey, I downloaded the kubuntu-live iso to try out KDE and when I select "Write to disc" or actually just try and write anything to the disc (either by copying it into the cd folder or through right clicking the file in nautilus,) I get a prompt saying:

"Insert a rewritable or blank disc

Please put a CD-R/CD-RW, with at least 643 MB free, into the drive."

The discs are memorex 700mB cd-rws and the drive I'm not sure as to the specifics but it says "CD-Writer Plus" on the font and it came from my old hp pavillion. The drive is detected in the device manager and when I put a blank CD-RW in I get the prompt for what I want to do with it, but it always tells me to put a disc in with enough memory in. Once in, the places section in nautilus displays as "CD-ROM Disc." Would this say CD-RW if it recognized it as such? How can I burn to the discs?

---

### Post by BitTorrentBuddha on 2006-05-18
I just tried and it writes under Windows (on a different computer) so it's not the disc, it could possibly be the drive, or maybe how I hooked it up, I just plugged it in like a regular CD drive, with an IDE cable, the master drive being the CD-RW drive and the slave being a CD-ROM drive.

---

### Post by Sef on 2006-05-18
I had the same problem with Breezy.  It cleared up once I upgraded to Dapper, which is still Beta.

---

### Post by BitTorrentBuddha on 2006-05-18
I was actually considering upgrading to dapper earlier today (not related to this issue.) Would I be okay to upgrade to dapper in the state it's in right now? I'm not working on large, dead-line heavy projects or anything, just home use, maybe some homework here and there.

---

### Post by BitTorrentBuddha on 2006-05-19
Bah, forget it, flight 8 is out, I'll just go download that.

---

### Post by Lester Cottrell on 2007-05-09
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=1033608](http://ubuntuforums.org/showthread.php?p=1033608) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am now using Fiesty and I cannot write a to a CD although it looks like it is available.  I keep getting
"Insert a rewritable CD or blank disk".  I have a SONY CD-RW CRX 140E cd-rom drive.  results of 
les@les-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives

** (process:27506): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_empty_unknown

Drive:
  name:                 CD-RW  CRX140E
  device:               /dev/scd1
  door:                 closed
  type:                 CD-R, CD-RW, CD
  is mounted:           FALSE
  max read speed:       5645 KiB/s (CD 37.6x, DVD 4.1x)
  max write speed:      1411 KiB/s (CD 9.4x, DVD 1.0x)
  write speeds:         1350 KiB/s (CD 9.0x, DVD 0.9x)
                        1200 KiB/s (CD 8.0x, DVD 0.8x)
                        1050 KiB/s (CD 7.0x, DVD 0.7x)
                        900 KiB/s (CD 6.0x, DVD 0.6x)
                        750 KiB/s (CD 5.0x, DVD 0.5x)
                        600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 Unknown Media (blank)
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 0.00 MiB
---
Drive:
  name:                 LTN486S 48x Max
  device:               /dev/scd0
  door:                 open
  type:                 CD
  is mounted:           FALSE
  max read speed:       8467 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:      0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:
Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---
How do I fix this? I am still new to ubuntu, but I like all the stuff that works and at least it is not microsoft:( 
Thanks, Lester Cottrell

PS-GnomeBaker works so above is no longer a problem, although it still exists. LC

---

### Post by Michl on 2008-01-25
I have the same SONY drive with the same problem!  It was
great to find the very same problem here.  Brasero does not
work, but I will now try gnomebaker.

Michael

---

### Post by Michl on 2008-01-25
> **Lester Cottrell said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=1033608](http://ubuntuforums.org/showthread.php?p=1033608) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am now using Fiesty and I cannot write a to a CD although it looks like it is available.  I keep getting
"Insert a rewritable CD or blank disk".  I have a SONY CD-RW CRX 140E cd-rom drive.  results of 
les@les-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives


Thanks, Lester Cottrell

PS-GnomeBaker works so above is no longer a problem, although it still exists. LC

Yes Gnomebaker works, while Brasero and whatever is loaded with Feisty does
not work with the SONY drive.  If I knew how to do it I'd do one of those official
thanks.
M/

---

### Post by Michl on 2008-01-25
> **Lester Cottrell said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=1033608](http://ubuntuforums.org/showthread.php?p=1033608) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am now using Fiesty and I cannot write a to a CD although it looks like it is available.  I keep getting
"Insert a rewritable CD or blank disk".  I have a SONY CD-RW CRX 140E cd-rom drive.  results of 
les@les-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives


Thanks, Lester Cottrell

PS-GnomeBaker works so above is no longer a problem, although it still exists. LC

Yes Gnomebaker works, while Brasero and whatever is loaded with Feisty does
not work with the SONY drive.  If I knew how to do it I'd do one of those official
thanks.
M/

---

