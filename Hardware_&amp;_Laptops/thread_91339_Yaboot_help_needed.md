---
title: "Yaboot help needed"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by HackSawtooth on 2005-11-17
I just installed Ubuntu on my Power Mac G4.  It was working great.  But now I cant boot into it anymore, my computer just automatically boots into OS X.  I think this happened because I zapped my PRAM.  Please help me as Ive lost all access to Linux because of this.

By the way this is my first post to the Ubuntu forums.  I plan on sticking around for a while.  Ultimately Id like to see Ubuntu run faster and more efficiently on my machine than Mac OS X.

Anyway thanks for any help

Chris P

---

### Post by stuporglue on 2005-11-17
Hold down option before the bootup chime, and you should get a menu with all the boot volumes. 

(Obviously?) click the penguin volume. 

Once you're into Ubuntu, run "sudo ybin -v", that will update the openfirmware and hopefully fix everything.

---

### Post by HackSawtooth on 2005-11-17
Awesome!  I was wondering how to just tell my computer what drive I wanted it to boot from.  Anyway all is well now.  Ive configured yaboot.conf the way I like it.  Took me a while to figure out that I had to run Ybin to load the new settings.  Man does this old 2GB SCSI drive take a while to load Ubuntu.  I think its max transfer rate is 10MB/s.  Anyway within the month I will have a 9GB SCSI drive with Ubuntu on it with a transfer rate of 40MB/s.

Thanks a lot for the help.  I can already tell this forum is going to be an invaluable resource for me.

Chris P

---

