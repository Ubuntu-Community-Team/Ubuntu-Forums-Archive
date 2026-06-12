---
title: "Baldur's Gate Error"
date: 2008-07-10
forum: General Help
---

### Post by nebcanuck on 2008-07-10
I'm at wit's end trying to get the Baldur's Gate DVD edition to work on my computer.

I'm running an EeePC 701, with a USB DVD drive. I purchased the entire Baldur's Gate saga knowing that it was one of the few really fun games I would be able to run on the EeePC and under Ubuntu. Most games either don't work under Wine, or are too advanced to run on the simple Eee -- usually both.

However, BG has given me no end of pain. I'm running Wine 1.0, and the game installs just fine by going into the CD and using Setup.exe. The first run through seems to work perfectly, however as soon as I restart my computer, the game won't run. If I try to run it off of my USB stick by clicking on Baldur.exe, I get the Assertion Error message:

"An Assertion failed in D:\Dev\Chitin\ChDimm.cpp at line number 581
Programmer says: Unable to open BIF:data\SFXSound.bif"

If I run it off of the CD using BGMain.exe or Autorun.exe, I get the Assertion Error message:

"An Assertion failed in D:\Dev\chitin\Chitin.cpp at line number 1360
Programmer says: Error initializing key table, bad key file"

Both result in a runtime error that causes abnormal program termination.

I've tried different levels of installation, including recommended and full, but none seem to work to get rid of either error. I've also tried tips from [this post]("http://ubuntuforums.org/showthread.php?t=114106"), but the problem fails to be resolved -- although, admittedly, the fix doesn't look like it's solving anything in league with my own issue.

Any help would be appreciated! I like this game a lot, and it would be a shame if I can't play it, as it's one of the few I was looking forward to enjoying in the world of the Eee.

---

### Post by Vadi on 2008-07-10
I think your question would be better suited for the wine forum ([click]("http://ubuntuforums.org/forumdisplay.php?f=313")) or whatever support forum xandros have.

---

### Post by nebcanuck on 2008-07-10
I'm not running Xandros. I'll post under Wine, too, but I've been using Ubuntu on the EeePC, and I suppose I was wondering if this was an Eee-Specific problem or one that other people have encountered?

Perhaps it has to do with the USB DVD drive? Have other people managed to run the game just fine using Ubuntu and a USB DVD?

As I said, I'll post under Wine, but the Xandros forums would be completely irrelevant! :)

---

### Post by Vadi on 2008-07-10
It just might be a wine problem too. Check with appdb.winehq.org.

---

