---
title: "poor video performance on Thinkpad T23"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by jjf on 2006-03-05
Just this past week I got a Thinkpad T23 (PIII-M 1.13 GHz, 256mb RAM) and put Ubuntu Breezy on it.  The T23 comes with a S3 SuperSavage IX/C 16mb graphics chip (described [here]("http://thinkwiki.org/wiki/S3_SuperSavage_IX/C") on thinkwiki.org).

I know that 16mb on an old chip isn't much to go on, but I've noticed very poor performance in DVD playback and games (e.g. [Chromium]("http://happypenguin.org/show?Chromium%20B.S.U."), a scrolling shooter).  Chromium is unplayable because it is so choppy, and DVD playback stutters in Totem.  I booted into WinXP and DVDs played back perfectly.

So what's going on?  Is my graphics chip not a 3d accelerator?  I have no illusions of playing Doom3 on this little guy, but I would like a few pretty diversions every now and again.  And is there anything I can do to improve DVD playback?  I'd actually prefer to use VLC rather than Totem, but VLC won't play DVDs.  I guess it doesn't know where the codecs are.  How do I tell VLC that I have libdvdcss installed?

Thanks.

---

### Post by jjf on 2006-03-08
In case anybody searches the forum for this, I think I found the solution to jerky DVD playback in the wiki:

[https://wiki.ubuntu.com/RestrictedFormats#head-389f8b000408629ef4fbb99723cfe0133fe31e7e](https://wiki.ubuntu.com/RestrictedFormats#head-389f8b000408629ef4fbb99723cfe0133fe31e7e)

I still haven't figured out how to configure VLC and I think my graphics chip just isn't powerful enough for anything with 3D.  When you get less than 10 fps on your *screensavers* I think you have to rule out any hot run-and-gun action.  Pity, that.  :(

---

