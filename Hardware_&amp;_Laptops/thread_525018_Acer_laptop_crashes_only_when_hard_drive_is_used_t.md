---
title: "Acer laptop crashes only when hard drive is used to operate it."
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by randytuggle on 2007-08-13
I have an Acer 5100-3583 that I bought a few months ago. I just replaced the hard drive because the last one ended up going bad on me. I put a new one in today and the problems I had with the last one were immediately apparent on the new one,too. Here's what happens:

I can start the laptop and usually start the desktop OS - Windows XP dies (restarts after just a minute or two. With Windows XP, I truned off auto-restart so that I would just get the BSOD. It looks like a syptom of motherboard issues but I'm unsure... let me go on becasue this is TOO ODD!

If I run Ubuntu or any OS on the hard drive, in time - that OS will freeze up and the power button must be pressed to shut the laptop down. RSEIUB doesn't do sqaut.

Since the old drive gave me problems -and before I got the new one today - I have been using pendrive linux (debian) from a persistent installation to a Sony USB Flash key drive. Here's my question; If my laptop  has a bad motherboard or bad memory (RAM), why does the USB drive operate fine and the hard drive fail? I wish I could just use pendrive linux and have the hard drive for a large storage area or something as this computer is a real problematic laptop! MEMTEST runs for at least 30 minutes and shows no errors,too. Please help if you know what is going on... THANKS!

---

### Post by shad0w_walker on 2007-08-13
Seems as it only happens when its running from the hard drive and most modern systems should be able to map around dodgy memory areas relatively well the odds are you have a problem with your IDE controller. Not fun, i would recommend contacting Acer and talking about repair/replacement assuming its still under warrenty.

---

### Post by randytuggle on 2007-08-14
ok - I might have gotten around this problem...

I installed a jumper on the hard drive because it was running without one (manufacturers don't add jumpers anymore that I see). I put a block on it to make the drive cable select. It seems BETTER now. Thanks for the IDE info! Ubuntu forums are the ONE AND ONLY! I can't believe how great this place is. Ubuntu rocks! Nothing is ever perfect - but at least Ubuntu users work on things. :)

X THAT! That didn't work! The CD-ROM/DVD drive does the same things,too. The CD-ROM drive will occaisionally act as if I have inserted a CD into the drive - which I haven't. I get a dialog box on the desktop asking me whether I want to load the CD media files or ignore ---- I just click IGNORE. At that point (a moment or two later at the longest) I will get a steady hard drive light on the keyboard and the system will lock/crash.

---

### Post by randytuggle on 2007-08-15
If the IDE controller is the culprit, could I disable the CD-Rom drive and bypass the problem until I can afford a new computer? How would I disable the CD drive?

---

### Post by shad0w_walker on 2007-08-15
There may be a setting in your BIOS to disable the cdrom drive. Usually have to hit the Del key to get into the BIOS, it will say somewhere during boot what key you have to press.

---

### Post by wildekek on 2007-10-28
Same laptop, same problem. I also bought a new harddrive which didn't fix it and replaced all my RAM. I just placed the jumper on the harddisk, let's wait and find out if it works.

---

### Post by randytuggle on 2007-10-28
I had this problem and realized that the IDE controller on the motherboard had to be the problem. I sold it and bought a 395.00 Acer at Walmart. No more problems. Sorry, but I think that's what you're dealing with.

---

