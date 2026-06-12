---
title: "Can't see the GUI"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by HoboGod on 2009-03-31
I just built a new computer:
AMD Phenom II x4 940 BLK 3.0G RT
Asus M4A79 DELUXE 790FX RT mobo
4 gig corsair RAM
1TB hitachi hard disk
LG blu-ray burner(DVD/CD as well)
two HIS ATI RADEON HD 4870s crossfire 1gig(I guessed that Ubuntu won't do crossfire, so I disconnected it)
PSU CORSAIR|CMPSU-1000HX 1000W RT power supply
and a Acer H213H21.5" 5ms HDMI Full HD 1080P Widescreen 16:9 LCD Monitor


...and installed both XP pro, and Vista business. so I figured I had enough room on my 1TB hard disk for some linux, I tried the live disk, but I could not see the installer, or even use the 'try Ubuntu' feature. so I went and downloaded the text installer, threw it on a cd and installed Ubuntu, then when it came time to restart my computer, I let it do so, it loaded, did the Ubuntu with the loading bar underneath, but then the screen went black(at first white), and just sat there, I am assuming it is my video cards, but I'm not compleatly sure. Would it be better to just install it in a virtual machine in Vista, or some such. I have used Ubuntu several times before, some earlier versions, in virtual machines, and on older computers, and never had this problem.

---

### Post by HoboGod on 2009-03-31
I suppose I can try this, but my mobo doesn't have any integrated graphics so I'm not to sure
[http://ubuntuforums.org/showthread.php?t=1037268&highlight=ATI+4870](http://ubuntuforums.org/showthread.php?t=1037268&highlight=ATI+4870)

---

### Post by Mark Phelps on 2009-03-31
> **HoboGod said:**
> I just built a new computer:
Would it be better to just install it in a virtual machine in Vista, or some such.

Yes...

>  I have used Ubuntu several times before, some earlier versions, in virtual machines, and on older computers, and never had this problem.
That's because your "older computers" had older hardware in them -- hardware for which there were Linux drivers.

Don't have an ATI HD card, so I can't attest whether or not the open source drivers can handle HD cards.  If you go to the Audio and Video subforum, you'll see some posts about installing the proprietary ATI drivers.  You'll need to download and install the Catalyst 9.3 drivers.

---

