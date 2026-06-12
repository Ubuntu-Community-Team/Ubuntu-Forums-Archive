---
title: "Ran S.M.A.R.T and No Errors, But Hard Drive Acting Weird"
date: 2012-03-31
forum: Hardware
---

### Post by playing_with_matches on 2012-03-31
So I ran the smartmontools in the Ubuntu Live CD (I did a full test), and it's showing that there aren't any errors at all.  However, I am having an issue where I get an error "partition doesn't exist" or "read error" when I attempt to boot my PC. 

Right before I started getting these errors, my Ubuntu and Windows (booted from HD) would run really really slow and crash horribly like it never has before.  Note that I could sometimes get to the GRUB screen and boot, but sometimes it throws errors.

What gives?  Is my hard drive dying even though smartmontools tells me everything is fine?  Any help is appreciated!  Thank you!

---

### Post by Yellow Pasque on 2012-03-31
I would try plugging it into another port (it would be even better if you had an auxiliary SATA controller or card).

---

### Post by ahallubuntu on 2012-04-01
Out of curiosity, have you tested the power supply on this computer?  Or tried a different power supply? Or did you recently add more components (new video card for example) to this system that could put a higher load on the power supply?

Power supplies can fail in really weird ways and cause unpredictable results.  I had a power supply fail a couple of weeks ago.  The power supply still showed good on the tester, but the main operating system drive would no longer be recognized by the BIOS on the original machine.  I thought the drive had completely failed, but connected to another computer, the drive was fine and showed no S.M.A.R.T. issues.  Swapping out the power supply completely fixed it the original computer and allowed OS drive to boot again, though the bad power supply did cause a corruption on another drive that was on that system.  


Lesson learned: don't use cheap power supplies, even if they test out fine.  Good name-brand power supplies can be had cheaply on sale if you look - for under $30 sometimes after rebate.  I've been buying them to replace older supplies, to avoid future problems in my systems.

---

### Post by playing_with_matches on 2012-04-01
I did add a new component come to think about it.  I added a new Optical drive.  I learned my lesson with power supplies a while ago when a cheap one malfunctioned and fried my MOBO, video card, and processor.  Definitely only get name brands now.  

I think the SATA thing might have been the issue!  It looks like I had the HD in Sata2 and the dvd in Sata1.  I switched it and haven't had any issues since, but if I continue to have issues, I'll suspect the power supply and go down that route.  Thanks guys.

---

### Post by ahallubuntu on 2012-04-01
I didn't mean to suggest that the power supply WAS your problem, only that it's one more thing to consider if you can't figure out the issue otherwise.  Power supplies can be had so cheaply on sale that it's almost silly not to have a spare in my view - and then it's pretty easy to swap supplies if you have any doubts.  You can buy a power supply tester as well but they aren't 100% foolproof. 

An extra optical drive should not take much more power - I think they take only about 10 watts.  But a new gaming video card could take 100watts or more by itself.  That's the kind of addition to a system that could cause problems like you describe, not an optical drive most likely.

But it sounds like you may have figured it out - good for you!

---

