---
title: "Is my CPU dying?"
date: 2010-10-12
forum: Hardware
---

### Post by ace214 on 2010-10-12
My computer is hanging randomly- I just upgraded it to Maverick a few days ago and went to update it. During the update it froze. I finally tried the terminal and got some output.

The [first image]("http://dl.dropbox.com/u/143104/IMG_3557.resized.JPG") is from a normal boot, but using the CTRL-ALT-F1 to get to a terminal. I think there may have been some text cut off.

The [second image]("http://dl.dropbox.com/u/143104/IMG_3558.resized.JPG") is from a recovery boot. You can see the upgrade process in the first line.

Can anyone translate? I built the PC in 2005. It has an AMD Athlon 64 3500 on an ASUS A8N-SLI motherboard with a Radeon X300SE video card.

---

### Post by Werm on 2010-10-12
Well that error is a MCE error. "4 Bank 4: b20000000070f0f"

Bank 4 &#8211; Northbridge and DRAM.

That's what the error is telling you. It looks like you may have some faulty ram. I'd run memtest+ and see, one stick at a time. The "northbridge" is what controls your ram and graphics

---

### Post by pricetech on 2010-10-12
Agreed.  Check your RAM First.

---

