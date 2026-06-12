---
title: "graphics cards"
date: 2011-09-29
forum: Hardware
---

### Post by Ms. Daisy on 2011-09-29
Hello All!  I have a bit of a chicken-and-the-egg problem.  It seems that I must first learn Ubuntu in order to install Ubuntu so that I can learn Ubuntu...

I installed a new hard drive in an HP Compaq (circa 2004).  It has no operational optical drive.  I installed Ubuntu, but Unity failed to install because the graphics card isn't big enough to handle it.  It's part of the motherboard.  So I installed a new (to me) [FONT=Calibri]PNY Verto GeForce FX 5200 [/FONT]graphics card (via PCI port).  However, I don't have the slightest idea how to convince the computer to use the new graphics card.  If I had a separate old one I could just unplug it.  But sadly it's onboard, so I suspect I will have to disable it.  I found a few threads along these lines, but they didn't quite apply to my situation.    

Any advice from the Ubuntu masters out there would be greatly appreciated.  (I know I should just buy a new computer. But surely I can't be the only person who has tried this!)

---

### Post by An Sanct on 2011-09-30
Welcome to the forums!

There has to be a way, to disable integrated graphics in BIOS.

If the monitor is plugged in to the new graphics card, it should all work normally. The only problem is, if your card is not strong enough for Unity, then a fallback will option is present (Unity 2D)

Also check "Additional drivers" and if a driver is available and enable it.

---

### Post by mörgæs on 2011-09-30
Ubuntu 11.04 has a problem with FX 5200. You could try Xubuntu in stead.

---

### Post by Ms. Daisy on 2011-09-30
Yes, I had an "aha!" moment earlier today when I realized I should just change the BIOS order.  Then I felt stupid for not thinking of that in the first place.   

I'm now successfully running Ubuntu 11.04 on my franken-machine.  So I think I overcame the problem with FX 5200.  Or at least I haven't encountered problems yet.

---

### Post by mörgæs on 2011-09-30
Good, then please mark the thread 'solved' using 'thread tools'.

---

