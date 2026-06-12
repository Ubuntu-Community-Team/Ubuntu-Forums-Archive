---
title: "WD4000AAKS HDD issues."
date: 2009-01-02
forum: Hardware
---

### Post by Judgie on 2009-01-02
First of all i'd just like to introduce myself.

My name's Michael, I live in good old dry, dusty and 3 years+ in drought South Australia, am a computer enthusiast and am soon to begin my final year of a Bachelor's degree in Environmental Management (a strange combination I know).

My query relates to some issues i've been having with the above mentioned model of SATA HDD by Western Digital, 5 months old since purchase and installation by myself, and which has played host to a standalone Windows XP installation for a few weeks, before having Ubuntu 8.04 and then 8.10 installed, and a reversion to a standalone installation of XP again while I figure out how to dual boot it (which I haven't started on yet).  From new, and currently whenever XP was (and is) installed and running, the drive makes a loud clicking noise when doing intensive reading and/or writing to/from the drive, not unlike the noise you hear during load/unload cycling of the heads, a problem that many of you with laptop installations may have experienced recently (excessive cycles). However SMARTmon tools shows only 399 such load cycles since new, 399 start/stops since new and 393 power cycle count. There have been 89 power retract off counts, 6 UDMA CRC errors, and the drive has total operating hours of 746. All other counters read Zero.  SO...... excessive load/unload cycles are likely not the issue. The drive is reported as HEALTHY and in good condition by SMART.

On top of this the drive never made the loud clicking noise mentioned above EVER while running the Ubuntu installations. Not once. I know this is a linux forum, but since many of you appear to be very knowledgable, more so than myself, do any of you have a solution as to what the issue may be when running windows?

As a side note, the drive failed to boot this morning, throwing an "disk read error has occurred " after POST and before the XP boot screen. For some reason it also prevented the recovery disk from loading as well, until I put in an older IDE drive I had and made that the primary boot HDD, which allowed the disk to load. I have resolved the "disk read error has occured" issue by executing the "fixboot" command in the recovery console and can operate the system again (have also backed up all data to another system again :D), but am wondering if this is related at all. From some googling, it appears that failures with this drive are not uncommon, which is amazing to me, as I have always used and never had problems with WD drives until now.

Thanking you all in advance.

M Judge
SA 
AU

---

### Post by cariboo on 2009-01-02
I would suggest you go [here]("http://support.wdc.com/product/download.asp?modelno=WD4000AAKS&x=9&y=7") and use the diagnostic software to determine whether your hard drive has a problem. Seeing as it is only 5 months old, if it is going defective you should be able to get a replacement drive with no problem.

JIm

---

### Post by Judgie on 2009-01-02
Thankyou for your reply! :)

Testing is underway as we speak (I actually started before checking the forums for any replies). It seems strange to me that a drive that is otherwise performing so well (very fast!) has such an obscure issue. Of note is that the drive is 21 minutes into the intensive extended test, and apart from normal read/write noises, I have yet to hear any of that annoying obscure loud clicking I mentioned except for a very short burst (<1 second duration approx.) about 9 minutes in.

Cheers
Mike

---

### Post by Judgie on 2009-01-02
The drive successfully passed the Datalifeguard diagnostic extended test. No bad sectors. Apparently this also means the MBR and Boot Sector are fine, as Chkdsk also reports. Did not hear any other annoying loud clicks during the test apart from what I reported in the previous post. As far as Datalifeguard, chkdsk and the drive's S.M.A.R.T. firmware are concerned, there are no problems. Given that these clicks do not occur in Ubuntu, but do in Windows (I have no MB case speaker hooked up, the drive is making the sound) it may well be a Windows specific *quirk* ?

I'd still like to know why it does it, but have been unsuccesfull in finding any related info on the net, and i'm not expecting much back from WD.

Cheers all.

Mike


EDIT:

I've decided to pick up a Seagate 500gb drive to replace it tommorow morning. If anyone finds out anything more about the problem above, please post in this thread.

---

### Post by Judgie on 2009-01-02
Here is a zipped .mp3 recording done with my mobile phone held within a centimeter of the drive, during a virus scan with AVG, recorded tonight. If you have the volume on your speakers way up and preferably use headphones, you can hear the sound of the system fans, the spinning platters and barely the sound of the drive being read, punctuated every so often with the comparatively loud clicks I have been writing about.

Cheers all.

Mike

---

