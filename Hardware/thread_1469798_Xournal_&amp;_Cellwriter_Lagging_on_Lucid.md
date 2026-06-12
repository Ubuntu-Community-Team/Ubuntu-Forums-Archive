---
title: "Xournal &amp; Cellwriter Lagging on Lucid"
date: 2010-05-02
forum: Hardware
---

### Post by marc1uk on 2010-05-02
I've had Ubuntu working on a Fujitsu T1010 tablet since Jaunty, and after the initial setup it's worked better as a tablet in Ubuntu than it has done in windows. Unfortunately that's no longer the case since an update to Lucid, with strokes now lagging in `applying ink' in both cellwriter and Xournal. The cursor moves, but ink only starts to appear after a delay - when writing this means the first half of every letter gets omitted, making e's appear as c's or E's as a sort of | : etc. 

Has anyone else had this issue or know any fixes? The only info i can find is a mention in [http://ubuntuforums.org/showthread.php?t=1386122&highlight=lynx+tablet](http://ubuntuforums.org/showthread.php?t=1386122&highlight=lynx+tablet) this thread about the removal of HAL - though the tablet screen in my T1010 isn't wacom (it's a unique passive usb touchscreen afaik.)

Any comments would be appreciated, I'd rather not have to go back to using Karmic, as i'm otherwise very happy with Lucid.

---

### Post by Favux on 2010-05-02
Hi marc1uk,

Do you know what driver the tablet is using?  If it's evtouch you might be able to play with some parameters.

---

### Post by marc1uk on 2010-05-02
> **Favux said:**
> Hi marc1uk,

Do you know what driver the tablet is using?  If it's evtouch you might be able to play with some parameters.

I found the driver on this site: [http://spareinfo.blogspot.com/2009/07/linux-on-fujitsu-u810-p1620-t1010.html](http://spareinfo.blogspot.com/2009/07/linux-on-fujitsu-u810-p1620-t1010.html) It's worked like a charm so far. Plus the actual tablet response is still fine - the cursor tip appears and tracks the stylus, just no ink comes out. Though it seems odd it should be happening with  both applications...

---

### Post by Favux on 2010-05-02
Hi marc1uk,

I've seen that site and the fujitsu touchscreen driver before.  I think maybe evtouch would also work.
> the actual tablet response is still fine - the cursor tip appears and tracks the stylus, just no ink comes out.
That is strange, it may be a bug in the applications if you're seeing ink in other applications.  In Xournal have you tried messing with some of the Options, like use Xinput?

---

### Post by marc1uk on 2010-05-03
> **Favux said:**
> Hi marc1uk,

I've seen that site and the fujitsu touchscreen driver before.  I think maybe evtouch would also work.

In Xournal have you tried messing with some of the Options, like use Xinput?

Just gave it a go now; no effect. Being a passive touchscreen it doesn't have pressure sensitivity, buttons on the pen or an eraser tip etc, so it shouldn't be any loss to not have it working, if that'd help.

> **Favux said:**
> 
That is strange, it may be a bug in the applications if you're seeing  ink in other applications.

Probably made this obvious, but ink does appear in both xournal & CW, just with a lag after putting stylus to screen.

---

### Post by Favux on 2010-05-03
> Just gave it a go now; no effect. 
Too bad.
> ink does appear in both xournal & CW, just with a lag after putting stylus to screen.
Right, I should have said if you are seeing ink _immediately_ in other applications.

---

### Post by marc1uk on 2010-05-03
> **Favux said:**
> Too bad.

Right, I should have said if you are seeing ink _immediately_ in other applications.

Ah, in that case I'm not - Xournal and CW are the only two pen-based applications i tend to use, but testing out GIMP too (can't think of any others i even have) there's a similar lag in that. It seems to be affecting all pen based input...

---

### Post by Favux on 2010-05-03
Oh, in that case sure sounds like the driver.  Check the README that came with the driver and see if there are options like SpeedLevel or Threshold you can set.

---

### Post by marc1uk on 2010-05-03
> **Favux said:**
> Oh, in that case sure sounds like the driver.  Check the README that came with the driver and see if there are options like SpeedLevel or Threshold you can set.

Alas, no such help, the only settings are screen calibration to make sure the cursor follows the stylus. Since it seems to have been developed for passive touchscreens, there's no need for pressure thresholds/sensitivity or the like (not sure what speedlevel is). 

Thanks for sticking with this Favux.

---

### Post by Favux on 2010-05-03
Not a problem.  Only option I see at this point is to post at the driver site and ask for help.  I don't think we would get too far trying to play with Xinput or something.

---

### Post by marc1uk on 2010-05-03
> **Favux said:**
> Not a problem.  Only option I see at this point is to post at the driver site and ask for help.  I don't think we would get too far trying to play with Xinput or something.
OK, posted. Will report back if/when I get a response or any more info. In the meanwhile I've been trying out other causes of general tablet lag; turning Compiz off, disabling right-click on click-hold, neither with any luck. Checking system monitor also doesn't seem to indicate any excessive CPU or memory usage when using pen-based input.

---

### Post by tgalati4 on 2010-05-03
Just boot back into Jaunty.  You did set up dual boot?

Never trash a working system.

Unless you like pain.

---

### Post by marc1uk on 2010-05-03
> **tgalati4 said:**
> Just boot back into Jaunty.  You did set up dual boot?

Never trash a working system.

Unless you like pain.

A dual-boot with two almost-identical versions of the same OS? Not part of my regular routine I must admit. Nor would i say this is 'trashed' just yet, and if I do need to make notes, I've still got XP as a fallback. 

Never uninstall windows. :)

---

### Post by tgalati4 on 2010-05-03
Yes, it sounds crazy, but if you install Lucid, it could take 6 months to get all of the fixes in place.  Otherwise your only fallback is Windows.  That's a level of pain only slightly above a borked linux installation.

---

