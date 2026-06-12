---
title: "Dell Inspiron N5010 click of death?"
date: 2012-06-30
forum: Hardware
---

### Post by rI9^)wx! on 2012-06-30
Hello all, I am experiencing a (very frightening) problem with my Dell Inspiron N5010. I have owned it for about 7 months now, and some time ago, I noticed a small click, click, click sound emanating from my laptop. Whenever it starts clicking, the hard drive light flashes. If it is repeatedly clicking, the hard drive light stays on. Is this just hard drive parking i am hearing, or the click of death? Also, perfect timing; I just ordered an Alienware M14X, and a few weeks ago I purchased an external HDD. Oh, and one last thing; when I turn on my laptop cooling pad, the clicking mostly stops. Please help!

---

### Post by westie457 on 2012-06-30
> **darkness3560 said:**
> Hello all, I am experiencing a (very frightening) problem with my Dell Inspiron N5010. I have owned it for about 7 months now, and some time ago, I noticed a small click, click, click sound emanating from my laptop. Whenever it starts clicking, the hard drive light flashes. If it is repeatedly clicking, the hard drive light stays on. Is this just hard drive parking i am hearing, or the click of death? Also, perfect timing; I just ordered an Alienware M14X, and a few weeks ago I purchased an external HDD. Oh, and one last thing; when I turn on my laptop cooling pad, the clicking mostly stops. Please help!

That sound is not good at all. Something is getting too hot and is stopping the platters from rotating. Stop using that hard rive before it dies completely. Fortunately you can still use Ubuntu in a Live Desktop either with a CD or USB-stick, you will not be able to save anything to the hard drive.

---

### Post by rI9^)wx! on 2012-06-30
OMG! Don't worry, I'm backing up my files as I speak! Also, I am pretty sure Dell warranty will cover a failing hard drive. And, my Alienware is coming in 17 days, so AMAZING timing! :KS Thanks for your help, I will be very cautious. I also installed Ubuntu to an external hard drive, I will use that instead.

---

### Post by westie457 on 2012-06-30
Good idea on backing up while the drive is still working, also for the install to an external drive. However if you are thinking of installing Ubuntu onto the Alienware search these forums for any issues that might happen.

Good luck.

---

### Post by ahallubuntu on 2012-06-30
Feel lucky if you don't lose any of your files - many people don't have backups and wait until their hard drive completely fails, then they lose everything.

You can check your drive's S.M.A.R.T. status using GSmartControl (install it in Ubuntu), to verify it's really a hard drive issue - but it sure sounds like it.

If under warranty, Dell will probably just send you a replacement drive and you send them the old one back.  First, they'll probably have you do their own diagnostic test over the phone, and if you don't have Windows anymore, I'm not sure how they will support you.  But having the S.M.A.R.T. info at hand could speed things up.

If the drive is really about to fail, you may not be able to clone it to a new drive (even if you can get your important files backed up) so expect to re-install Ubuntu from scratch on a new drive.

---

### Post by rI9^)wx! on 2012-07-04
A new hard drive has arrived, and the data has been successfully transferred! I checked with gsmartcontrol (or something similar) from the Parted Magic CD. 3 of the values were displayed as "Pre-Failure"! I'm glad all my data is safe on my new hard drive. Remember, if you hear a click, make a backup real quick! And thanks for your help!

---

### Post by ahallubuntu on 2012-07-04
> **darkness3560 said:**
> A new hard drive has arrived, and the data has been successfully transferred! I checked with gsmartcontrol (or something similar) from the Parted Magic CD. 3 of the values were displayed as "Pre-Failure"! I'm glad all my data is safe on my new hard drive. Remember, if you hear a click, make a backup real quick! And thanks for your help!

"Pre-failure" doesn't mean the drive was about to fail.  Many healthy attributes are of the "pre-failure" type. (Try your new hard drive - same thing, right?)  Attributes that are highlighted in Red are the ones you should worry about.  "Pre-failure" just means a type of attribute, not a status.

---

