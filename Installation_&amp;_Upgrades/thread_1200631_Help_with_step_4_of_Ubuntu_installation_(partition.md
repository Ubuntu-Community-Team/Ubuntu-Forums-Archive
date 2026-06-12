---
title: "Help with step 4 of Ubuntu installation (partitioning)!"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by DarkDjango on 2009-06-30
I'm trying to install Ubuntu on a laptop with a brand new HD and when I reach step 4 (partitioning) I am not given the options I should be given for a "Guided partitioning" but instead I am given a blank table with absolutely no options to choose from and the only available actions are to cancel the installation or attempt to go forward and receive an error message that says "no root file system is defined. Please correct this from the partitioning menu." However, as I stated, there are no options to choose from on the partitioning menu, only a blank table!  HELP!!!

---

### Post by philcamlin on 2009-06-30
its not detecting your hdd

do you have any more in your pc other then one?

if you do turn them off in your bios then try again

---

### Post by DarkDjango on 2009-06-30
nope, just the one.  It's a toshiba laptop and the HD is brand new.  What can I do?

---

### Post by DarkDjango on 2009-06-30
I've never installed a new HD before.  I just plugged it in where the old one was.  Is there some step that I have missed before attempting Ubuntu installation?

---

### Post by sirhalos on 2009-06-30
There is nothing you need to do however you should go into your BIOS and make sure your laptop sees the hard drive. Usually when you boot up your laptop it will be pressing Esc, F2 or F10 some are even Del it goes by pretty quick so you need to be fast. From there you can see if your laptop sees the hard drive.

It may be possible if it's an older laptop but a newer hard drive that your laptop does not support a larger drive (say one over 80 gig). Older laptops were like that, luckly a lot of them were fixed through BIOS updates.

So I would say step one, go in your BIOS see if your laptop sees the hard drive.

Step two if it sees the drive it shows an odd amount like 47 gig or something instead of 120 gig than you need to go to Toshibas website and search your model number for a BIOS update (if they have one).

If all that is good you should be good to go with the install. You can drop to at root window and type fdisk if you want to see if Ubuntu sees it.

---

### Post by gchand7 on 2009-06-30
I ran into this once. I had to format a drive in windows. then reinstall it in the computer so the motherboard could recognize it. Gparted will most likely do it in Ubuntu. You may even be able to do it in the live mode.

---

