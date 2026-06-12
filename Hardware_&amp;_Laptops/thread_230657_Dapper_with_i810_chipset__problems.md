---
title: "Dapper with i810 chipset : problems"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by dusu on 2006-08-06
Hi,

I've got an old toshiba laptop (S3000-X4), which perfectly ran Hoary, and on which I now fresh-installed Breezy, which also perfectly works.

I thought I could install Dapper on it, since old hardware should be recognized in newer versions... that was a mistake.
I cannot get a proper Xorg configuration that makes my screen working :(
It seems there's a problem with Xorg7, which is really a pity.
I've tried both an upgrade from Breezy and a fresh install, but nothing does.

I'm not expecting anyone to fix this, I'm a (very) happy Breezy user.
This thread is more intended to potential users who would feel like installing Dapper on a computer with i810 chipset !
Be aware some problems are waiting for you on the way !

---

### Post by er-ku on 2006-08-06
well, i'm running dapper on a computer with an i810. What's your exact problem? Have you checked /var/log/Xorg.0.log for lines with "EE"?

---

### Post by dusu on 2006-08-06
> **er-ku said:**
> well, i'm running dapper on a computer with an i810. What's your exact problem? Have you checked /var/log/Xorg.0.log for lines with "EE"?

Hi er-ku,
thanks for your post. I add checked for lines with "EE" in /var/log/Xorg.0.log, but as I do not have Dapper installed any more, I can no longer tell you what they were.

My exact problem is the following :
 - trying to boot with the Dapper CD, the screen turns black at the point where Xorg is being configured, so I cannot even use a live Dapper :(
 - the same happens to me if I install Breezy Desktop then upgrade to Dapper
 - I even tried installing Breezy server, upgrading to Dapper, then doing everything I know how to do with Breezy, to get X working : no way...

In fact, doing some dpkg-reconfigure xserver-xorg, and choosing vesa instead of i810 leads me somewhere : x starts, but it's so ugly and useless :(

But I'm glad to hear one can make it work. Let's say I'd like to get the live version working before I get rid of my brand new Breezy !

---

### Post by er-ku on 2006-08-06
Well, a friend of mine had a similar problem with err... I think, ATi or Nvidia video.

Anyways, i810 drivers are at least open and these should really work. Maybe the problem was that they were trying to use the external monitor (which wasn't of course connected) or setting a resolution too high for your hardware? Both of these problems can be easily corrected (of course, it'd be better not to face them at all, but we both know that Ubuntu guys cannot test every possible hardware configuration for us).

P.S. my i810-based computer is not a laptop after all.. :)

---

### Post by dusu on 2006-08-06
Well, I guess there is a difference here between your case and mine, and you're probably right somehow :
when doing sudo dpkg-reconfigure xserver-xorg, my i810 car is seen, but it's when Xorg tries to figure out what my screen is that the trouble arises...

well, anyway, Breezy rules :D, though I'm a bit frustrated not to have Dapper running :???:

---

