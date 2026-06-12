---
title: "Ubuntu 11.04 and the graphics/screen problems"
date: 2011-06-03
forum: Hardware
---

### Post by Smithie on 2011-06-03
Hello,

I just upgraded from 10.10 to 11.04 and my dual screen system is an absolute mess.  Images freeze and leave lengthy trails, etc.  The dual screens function fine in Ubuntu classic (no effects), and of course worked fine in 10.10.  So, I assume this is a conflict between "compiz" and "unity".....but, I don't really know what the heck that means.

My current hardware is:
CPU: Intel Pentium D 2.80GHz
Video: ATI RV370 5b60,   Radeon X300 (PCIE)
Mem: ATA SAMSUNG HD502HI

So, is there an effective work around to make this video card function or do I need to bite the bullet and replace the video card with an nVidia?  If there is a work around, please give me the basics in the description as my terminal use is rookie at best.

Thanks!

---

### Post by Smithie on 2011-06-04
Well, after attempting a series of fixes, it became pretty clear that my old ATI video card was no longer supported by the new proprietary drivers and none of the open ones resolved my issues in 11.04.  I switched to an nVidia 8400GS.  Now, at least, I have the same monitor, display, and unity problems that everyone else is dealing with....:(

Pretty unhappy that 11.04 was released out of beta with these bugs still in it.  Seems many, many folks with a both ATI and nVidia systems are having a lot of issues.

If these releases need to come so quickly, I really wish the Ubuntu folks would think about installing an easy to use "downgrade" feature, so you could at least wait out the newer version bug fixes in a more stable and pleasant OS.  It's too bad to, I was recommending Lucid and Maverick to anyone who was interested.  I will certainly be far more guarded about that now.

---

### Post by halversondm on 2011-06-06
I'll have to second the hardware issues.  I had 9.10 installed up until a few days ago.  I didn't upgrade to 10.04 or 10.10 due to networking issues.  Then I installed 11.04 because Update Manager said that my version was no longer supported.  Now my networking issue appears to be resolved, but there appears to be some issue after login with the graphics card.  It's an nVidia FX 5500 chipset, old, but not broken.  I'm not positive of the graphics card issue yet, but I'm fairly certain that when the open windows are flashing at you and there is no menu bar, there's probably a driver issue of some sort.  I'm going to try the nomodeset option later today to see if that fixes the issue.

Funny thing is that I used the same install CD on a laptop one year newer than the desktop and had no issues whatsoever.
 
Dan

---

### Post by Yellow Pasque on 2011-06-06
Question: did the ATI card work with regular Gnome/Compiz or was it just Unity that screwed it up?

---

### Post by Smithie on 2011-06-07
As far as I know, it was unity.  10.10 worked absolutely fine, and in 11.04 ubuntu classic also worked.

---

