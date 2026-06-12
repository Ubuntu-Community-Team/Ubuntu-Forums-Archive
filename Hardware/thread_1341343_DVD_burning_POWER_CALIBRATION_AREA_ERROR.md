---
title: "DVD burning: POWER CALIBRATION AREA ERROR"
date: 2009-11-29
forum: Hardware
---

### Post by Jonathan Métillon on 2009-11-29
Hi,

I'm trying to burn a DVD+R (Verbatim media) with a [Sony Vaio VGN-TX3XP]("http://www.trustedreviews.com/notebooks/review/2006/07/25/Sony-VAIO-VGN-TX3XP-Ultra-Portable-Notebook/p1") (European equivalent to US TX610) on Ubuntu 9.10. The burner is a Matshita UJ-832D.

It used to burn very well on Ubuntu. But now I'm having the same issue described in the thread [Power calibration Error?]("http://ubuntuforums.org/showthread.php?t=915674")

I checked the firmware version running [DISCInfo]("http://discinfo.rpc1.org/") 1.7.0 BETA on wine. It says 1.61 and I can't find any newer version from Google and Sony Vaio support websites.

lshw outputs:

```
                description: DVD writer
                product: UJ-832D
                vendor: MATSHITA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.61
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc

```Brasero outputs:

```
BraseroGrowisofs stderr: :-[ WRITE@LBA=300h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stdout:     1572864/4699979776 ( 0.0%) @0.0x, remaining 2140:48 RBU  96.8% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stdout:     1572864/4699979776 ( 0.0%) @0.0x, remaining 2290:09 RBU  96.8% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1572864/4699979776 ( 0.0%) @0.0x, remaining 2439:31 RBU  96.8% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: closing track
BraseroGrowisofs stdout:     1572864/4699979776 ( 0.0%) @0.0x, remaining 2638:39 RBU  96.8% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1572864/4699979776 ( 0.0%) @0.0x, remaining 2788:01 RBU  96.8% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-[ CLOSE TRACK failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stderr: :-[ CLOSE DISC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```GnomeBaker outputs:

```
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
:-( write failed: Input/output error
```Any idea how to fix that... without buying a new burner? ;)

(Will buy a cleaning kit soon.)

---

### Post by salemboot on 2010-01-06
Couple of options:
Choose one or two of the following
1. Install schilings version of the DVDr tools. [http://cdrecord.berlios.de/private/cdrecord.html](http://cdrecord.berlios.de/private/cdrecord.html)
2. force the kernel to see your dvdr as ide
3. Install an older version of Ubuntu (8.04, 8.10)
4. Hope the ubuntu developers realize there is a problem and fix it by 10.x
 

I have the same problem.  Vaio's dvdr drive is finicky

---

### Post by Jonathan Métillon on 2010-02-22
Thank you very much Salemboot!

Actually I prefer to hear about an Ubuntu hardware support issue than a broken burner :P

Maybe I can help developpers realize there is a problem by submiting a bug report?

Won't install an older Ubuntu. But for suggestions 1 & 2:

Why is DVDr tools special? What is the schilings version? A paying version? (I'm not speaking English natively.)

How would I force the kernel to see my dvdr as ide? Why it sees it as SCSI?

Again, thanks!

---

### Post by Jonathan Métillon on 2010-11-01
Hi,

Almost one year later, trying to re-burn a DVD+RW (already burnt years ago). Still same errors.

Is there some news? I didn't update Ubuntu since a long time (using a MacBook Pro daily). I'm still on Ubuntu 10.04 LTS the Lucid Lynx. Maybe it's been fixed since then?

Thx!

---

### Post by IcarusR on 2010-11-01
Have you tried the obvious things, such as

Cleaning the laser lense.
Try other media, specifically 4x Ricoh DVD+RW. I have read on rpc1.org (firmware site) that they are notoriously fussy over media. And rated as c$£* dvd drives.
Try burning at a very slow speed.

Generally the "SK=3h/POWER CALIBRATION AREA ERROR" error is related to lack of power. So if this was a usb drive I'd suggest powering with an external brick.

You could try removing the drive & cleaning all the contacts & refitting.

Sorry not really any stunning suggestions I know but may help ??

---

### Post by Jonathan Métillon on 2010-11-01
> **IcarusR said:**
> Cleaning the laser lense.

Nop.

> **IcarusR said:**
> Try other media, specifically 4x Ricoh DVD+RW.

Neither. Again a Verbatim DVD+RW 2.4x.

> **IcarusR said:**
> I have read on rpc1.org (firmware site) that they are notoriously fussy over media. And rated as c$£* dvd drives.
Try burning at a very slow speed.

Matshita in general or the UJ-832D in particular?

> **IcarusR said:**
> Generally the "SK=3h/POWER CALIBRATION AREA ERROR" error is related to lack of power. So if this was a usb drive I'd suggest powering with an external brick.

It's not. It's the embeded drive you can see here from the product description in my signature, the Vaio TX3XP.

> **IcarusR said:**
> You could try removing the drive & cleaning all the contacts & refitting.

Will do!

> **IcarusR said:**
> Sorry not really any stunning suggestions I know but may help ??

Thank you! :)

---

### Post by Jonathan Métillon on 2010-11-01
Just upgraded to Ubuntu 10.10 and it's not better.

---

### Post by IcarusR on 2010-11-01
So try cleaning the laser lens, CAREFULLY.

> Neither. Again a Verbatim DVD+RW 2.4x.

So try a different make of disk, 4x Ricoh DVD+RW recommend on rpc1.org.
And burn at a SLOW speed, I normally do at 2x & leave it to do it's thing while I have a coffee.

> Matshita in general or the UJ-832D in particular?

Specifically the UJ-832D. But I would stay clear of them as a brand.

Maybe less hastle / stressful just to bite the bullet & buy a new drive, can't be that expensive. £30 - £50 here for latest sony.

---

### Post by mojotexas on 2011-04-19
I had the same error. The answer turned out to be just a lack of disk space, there wasn't enough room to create the temp files for burning the DVD. I deleted some files and that was that.

---

### Post by ktec on 2011-12-23
Experiencing same problems as you.

1. Its definitely NOT a problem of disk space.
2. It used to work fine back in ubuntu 9
3. I have cleaned the lense.
4. I have tried with various different burn tools - wodim/brasero etc
5. destroys every disc i throw at it

---

### Post by ravidborse on 2011-12-29
Hi All(Solved in my case)

  - To Resolve Below Error related to my Sony DVD-RW Just Remove your DVD-RW player
  - I used to get the  DVD burning: POWER CALIBRATION AREA ERROR in UBUNTU. and In fedora I get the below error. Both Error are same. And Below Steps work for me.
  -  Open it with the screwdriver(Its very Easy). Now you can see the Reader-Writer Lense . 
  [B]- Take any solution(Prefer Alcoholic or the solution you use it to clean LCD) and cotton. 
  - Use a cotton swab and something like alcoholic solution(small) to gently wipe the lens. Just a quick scrub will do. [/B]
  - Dry the laser pickup lens with the other end of the swab.Keep it 10-15 Mins to dry that lens. 
  - Do this carefully Please. I have done it on my own risk. you can also. below is the error


DVD-RW Sequential

Devices
-----------------------
SONY DVD RW AW-G170A 1.74 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.5.5 (KDE 4.5.5)
QT Version:  4.6.3
Kernel:      2.6.33.3-85.fc13.i686.PAE

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 2.0x1352KBps.
          0/669122560 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 20 times. ===
:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:326720 -dvd-compat -speed=2 -use-the-force-luke=bufsize:32m

---

### Post by overdrank on 2011-12-29
Hi and welcome, please view the date of the thread. Old thread = Closed thread.

---

