---
title: "hard drive prefailure?"
date: 2013-02-16
forum: Hardware
---

### Post by JohnDillinger43 on 2013-02-16
So I guess this isn't an OS-specific question, but I don't have a lot of experience testing hard drives in Ubuntu.  My concern is that my external backup drive (connected via eSATA) has started sporadically making a click of death sound.  However, it's not all the time, and the drive seems to function completely normally otherwise.  It passes the SMART tests; there are a few red flags in the attributes section (which, notably, my other drives do not), but nothing even close to the failure threshold.  If I catch it when it's clicking and access the drive, it works just fine and in fact stops clicking on access.  I have it doing nightly backups and haven't gotten any errors in the logs.

Obviously the safest course of action is always just to replace the drive.  But the drive's less than 2 years old, WD Black (which I've had nothing but great experiences with) in an external fan-cooled enclosure.  I've encountered the click of death after failure, as well as chirping on access pre-failure, but never this kind of clicking without any errors in reading from or writing to the drive.  Just wanted to get some feedback before jumping straight to a replacement.

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by tgalati4 on 2013-02-16
Open a terminal:

```
dmesg | tail -100
```

Plug in your eSATA drive and run dmesg after you hear clicking and see what messages come up.  It's possible you have a cable or connection problem, or the SATA chip on the hard drive is getting hot and crapping out.  SMART comes up OK, but communication is intermittent causing issues.

This has happened to me on some internal drives, and reseating cables took care of the problem.

---

### Post by JohnDillinger43 on 2013-02-17
@ahallubuntu:
Yep, I'm using GSmartControl.  I've never really understood all the SMART readout (Norm-ed value, Worst, Threshold, Raw Value), so I'll post a couple attributes here.

I have three flagged attributes:
5 - Reallocated Sector Count, raw value = 1, pre-failure
196 - Reallocation Event Count, raw value = 1, old age
197 - Current Pending Sector Count, raw value = 1377, old age

Is that last attribute the one you mentioned?  Because if so it looks like the drive isn't doing too well.  However, it is a backup drive, so if it crashes I wouldn't lose anything, just would want to replace it ASAP.

@tgalati4:
Thanks for the tip.  I actually haven't heard it click again since I posted here, but I'll check that out next time I hear it.

---

### Post by ahallubuntu on 2013-02-17
~

---

### Post by tgalati4 on 2013-02-18
Different drives handle pending sectors differently.  It's possible that it took 2 read passes (instead of one) to read those sectors.  Maybe the drive was cold, or hot, or tilted, or bumped.  Just keep a watch on it.  Monitor the temperature as well, if it climbs in temperature that might be an indication of bearing failure.  Clean out the machine and watch it.  Do some research on SMART parameters.  Each manufacturer defines the parameters their own way--so much for standards.  SMART only captures 2/3 of the failure modes anyway.  1/3 are not captured (like failing electronics) and cause the drive to die instantly, without warning.  So just be ready.

---

### Post by Vegan on 2013-02-18
get some more hard disks and make a backup

usb seem to be more stable than eSATA in my experience and USB2 is good enough for most users

USB3 is faster but USB3 cases are still expensive

---

### Post by JohnDillinger43 on 2013-02-19
Thanks for the advice everyone.  I ordered a replacement drive, and I'm going to replace the drive and check everything out to make sure it's not the enclosure.  I'll probably DBAN the old drive to see if it's still usable for anything.

---

### Post by SuperFreak on 2013-02-19
I just purchased a WD Black recently, mainly because of the 5 year warranty. Check your warranty on the drive it may be possible to get a free replacement

---

### Post by JohnDillinger43 on 2013-02-20
That's good to hear -- mine is also a WD Black, so hopefully I can get a replacement.

---

### Post by ahallubuntu on 2013-02-20
~

---

### Post by JohnDillinger43 on 2013-02-21
Excellent, I didn't realize GSmartControl showed the serial numbers there.  However, when I entered it on the WD site, it says invalid serial number.  I'll have to double check it when I actually take the drive out.

---

### Post by ahallubuntu on 2013-02-21
~

---

### Post by SuperFreak on 2013-02-21
Once you have entered the serial number to register the drive, the warranty period for your drive will display along with options for RMAing the bad drive. Good Luck

---

### Post by JohnDillinger43 on 2013-02-22
Hmm, the format I have is WDC WD2002XXXX-XXXXX, where all the drives start with WDC WD, followed by the size (well, I'm not sure if the size portion is 200 or 2002), followed by 4 characters, a dash, and 5 more characters.  I haven't tried all parsing combinations yet, but I can't get the site to validate my SN.

---

### Post by SuperFreak on 2013-02-22
Believe Western Digtal registered mine with a 12 digit S/N  with WCC followed by 9 numbers

---

### Post by JohnDillinger43 on 2013-02-25
Yeah...I was looking at the model number :/  Found the serial number, and it is under warranty, so I'm getting it replaced.  Thanks everyone for the help/advice.

---

