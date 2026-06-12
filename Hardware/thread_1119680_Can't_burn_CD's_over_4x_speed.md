---
title: "Can't burn CD's over 4x speed"
date: 2009-04-08
forum: Hardware
---

### Post by kWahab on 2009-04-08
Drive model is SONY DW-Q58A (came with my Dell laptop). The specs say it can write CD's at 24x. But if I set the speed over 4x in brasero or the nautilus cd burner the write fails. At 4x everything works fine.

cdrecord -prcap shows max (and the only) write speed as 4x.
what do I need to do to get a decent write speed?

the output of  cdrecord -prcap is:
```

Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD+-RW DW-Q58A '
Revision       : 'UDS2'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.

Drive capabilities, per MMC-3 page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does read DVD-ROM media
  Does read DVD-R media
  Does write DVD-R media
  Does not read DVD-RAM media
  Does not write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does not read R-W subcode information
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 256
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  1411 kB/s (CD   8x, DVD  1x)
  Current read  speed:  1411 kB/s (CD   8x, DVD  1x)
  Maximum write speed:   706 kB/s (CD   4x, DVD  0x)
  Current write speed:   706 kB/s (CD   4x, DVD  0x)
  Rotational control selected: CLV/PCAV
  Buffer size in KB: 2048
  Copy management revision supported: 1
  Number of supported write speeds: 1
  Write speed # 0:   706 kB/s CLV/PCAV (CD   4x, DVD  0x)

```

---

### Post by HermanAB on 2009-04-08
That is normal behaviour.  Few, if any writers work at speeds in excess of 8x, most work at 4x.  Never believe the sales literature with this crummy technology.

---

### Post by FrankT-Qc on 2009-04-08
Don't buy that ! I have been tossing quite a few burners around and always made it pretty close to the specs... Well there are a few reluctant drives out there...

Try burning an iso with 
```
wodim  speed=/path/to/someimage.iso
```
and see what it tells you... 

By the way, most burners are wise enough to query the media capacity (i.e. if you want to burn at 800X, you have to buy a CD/DVD that supports it ...). You don't have a 4X blank in there, do you ?

have fun,
Frank

---

### Post by kWahab on 2009-04-08
I'm talking about CD's not DVD's. I have a much older Plextor PX-S2410TU external laptop style drive that is also rated 24x and gives much better performance.
Anyway the Sony drive gives no trouble in windows with nero. I've tried many different media and they all give the same result.

Even if we consider that these x ratings are not reliable, i can still see the performance by the time it takes to burn CD's.

---

### Post by kWahab on 2009-04-08
> **FrankT-Qc said:**
> 

Try burning an iso with 
```
wodim  speed=/path/to/someimage.iso
```
and see what it tells you... 


I think you have the command wrong there. I just get an error
```

$wodim speed=/media/shared/downloads/ubuntu-9.04-beta-desktop-i386.iso
wodim: Bad Option: speed=/media/shared/downloads/ubuntu-9.04-beta-desktop-i386.iso.
Usage: wodim [options] track1...trackn

Use	wodim -help
to get a list of valid options.

Use	wodim blank=help
to get a list of valid blanking options.

Use	wodim dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.

Use	wodim dev=help
to get a list of possible SCSI transport specifiers.

```
My media says 52x :)
I would be happy with somthing around 12x.
going to try 
```

wodim  speed=12 /path/to/someimage.iso

```

---

### Post by kWahab on 2009-04-10
Great the CLI works now. The command
```

wodim  speed=24 /path/to/someimage.iso

```
was a complete success.

Thanks

---

