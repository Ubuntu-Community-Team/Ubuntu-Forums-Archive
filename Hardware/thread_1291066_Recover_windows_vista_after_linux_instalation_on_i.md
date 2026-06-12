---
title: "Recover windows vista after linux instalation on it"
date: 2009-10-14
forum: Hardware
---

### Post by sasingh on 2009-10-14
Hi All,
 
I've accidently done linux (suse 11.1) installation on windows (vista) partition of Compaq notebook ( windows vista home - basic pre-installed ). And now I am afraid that I might not be able to get back to the windows data. And, the big worry is that I've not taken backup of some important data. I tried using the Recovery CD but no go, as the windows hard drive partition has been over written by linux installation. Any pointer to recover the vista installation will be of gr8 help. 
 
Thanks

---

### Post by Giblet5 on 2009-10-14
If you really did install Linux over Vista, then the only way to recover the Vista data is to hire a data recovery service. That will be very expensive and it is unlikely that you will be able to retrieve everything.

---

### Post by bruno9779 on 2009-10-14
Since there is a change of file system between Win-dose and Linux, I think that is very unlikely you will recover anything at all even by hiring an expensive data recovery service.

---

### Post by Giblet5 on 2009-10-14
> **bruno9779 said:**
> Since there is a change of file system between Win-dose and Linux, I think that is very unlikely you will recover anything at all even by hiring an expensive data recovery service.

A single write-over is very recoverable and Linux has a small footprint.

All of the multiple writes will have occurred in the outer cylinders; right where the base Windows install would be located. The MFT, which is usually written 1/3 of the way in toward the spindle, may be completely recoverable and that's the biggest hurdle.

If the data is REALLY important/valuable, it's probably worth trying a pro recovery service.

I'd guess that's a $3,000-$8,000 test though, so it better be VALUABLE data...

---

### Post by sasingh on 2009-10-15
Hi,

Thanks to all for sharing your views.

---

### Post by Dark_Stang on 2009-10-15
Data recovery is usually $600-$1500. There are several companies that can do that for you if it really is that valuable. (geek squad and office depot to name 2)

---

### Post by garvinrick4 on 2009-10-15
Please make sure you screwed Vista, can you boot into it, if you can might be longshot
and can use system restore. May be something simple and silly but you never know. If it
boots or you can get into it at all their seems to be a lot of ways for Vista to recover. Check them all out.   If you just installed over it you can kiss the Baby goodbye. But you never know something simple, might be your lucky day or your moons are lined up or something. See ya

---

### Post by nzadLithium on 2009-10-15
You should be able to recover the data yourself using this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If your going to attempt that though I would suggest that you boot from a live cd and mount the hard disk in read only mode (actually im not even sure you have to mount it, so perhaps dont even mount it :D), otherwise its likely you'll overwrite more of the data you might be able to recover. Also you will need another disk (usb drive or hard drive) that is big enough to hold the entire restored partition. Also you should not boot that computer from the hard drive under any circumstances if you don't want to lose more data. Every time you go on the pc your computer will create and delete files of some description and every time it does this will likely cause less of the data to be recoverable.

---

### Post by sasingh on 2009-10-22
Hi All,
 
Thanks for sharing the pointers to recover lost partition. Although now i have installed windows xp, the resolution tips shared might help; if something like this ever happen again :)
 
-- Cheers

---

