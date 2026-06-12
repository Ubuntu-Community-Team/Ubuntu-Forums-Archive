---
title: "BIOS is acting up."
date: 2009-06-01
forum: Hardware
---

### Post by I am &gt;= Wes on 2009-06-01
So my friend's computer (an emachine) is broken.  It get's to the big "e" at boot up but can't get past that.  No f keys work, nor do I know of a single way to fix this problem.  I immediately thought it was a mobo issue.  My mother's computer is having a similar problem with her (dell) BIOS where any and all text has been changed with corrupted characters.  I read somewhere about some one with a problem exactly like that of my friends and they were told it was an EEPROM problem and that they should replace it.  I know this isn't specific to the Ubuntu community but I don't know who else I'd be asking; you all seem very trustworthy and helpful.  I'm curious if it's really that easy (to switch out an EEPROM) and if so where I could buy an EEPROM.

Many thanks,
--Wes

---

### Post by HavocXphere on 2009-06-01
> **I am >= Wes said:**
> I'm curious if it's really that easy (to switch out an EEPROM) and if so where I could buy an EEPROM.
3 things make it difficult: The mobo manufacturer must have designed the board to make the EEPROM removable. And secondly you need to find a replacement chip.

Fairly straightforward in theory...but finding a replacement chip is usually pretty close to impossible. (It's not like RAM where any damn thing will work) It needs to be *exactly* the right type.

And finally, the price of a replacement EEPROM is usually pretty close to that of buying a new motherboard.

---

### Post by I am &gt;= Wes on 2009-06-01
So, if replacing the EEPROM is out of the question does any one have any other ideas as to how I may be able to fix these problems?  If not, does any one know of a mobo that is the same size/shape as an ATI SB400? (in the emachine)

---

### Post by kerry_s on 2009-06-01
you could try reflashing the bios. if it is indeed a bios problem.
you need to look up the the key you need to press to get into the bios, as soon as you power on start tapping that key.

what your describing doesn't sound like a bios problem, so the only way your going to tell is to get in there. i've seen what your describing for bad disks where the bios just can't find the disk to continue. try a live cd.
bad ram can also do that, where it just locks up on the first screen. if you have 2 ram modules switch them around or pull 1 and try them separately.

---

### Post by I am &gt;= Wes on 2009-06-01
I've already tried livecd's, both a windows live cd and a Jaunty live cd, neither worked.  I also tried a live USB which also failed to work.  Any keys that are pressed to get into the BIOS are completely ignored.  I'm afraid it's a faulty mobo but I'm really banking on a BIOS problem.  Other than that I can't say what it is.

---

### Post by pricetech on 2009-06-01
Have you removed the CMOS Battery ??  That might reset things where you can get access.  Also try disconnecting everything you can (harddrive, floppy, cdrom) and if that gets you in then reconnect things one at a time.

---

### Post by I am &gt;= Wes on 2009-06-03
Tried the CMOS battery, tried the Clear CMOS thing, tried disconnecting everything.  Nothing.

---

