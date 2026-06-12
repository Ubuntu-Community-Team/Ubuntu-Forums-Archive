---
title: "Need help on how to install Xgl with Intel 945GM"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by DapperDrakeNewbieDR on 2006-08-30
Does anybody know how to install Xgl with Intel 945GM Express Chipset?

---

### Post by ayoli on 2006-08-30
Actually, i have an Intel i855GM chipset and i use aiglx/compiz which works great. i installed it fellowing [this howto]("http://ubuntuforums.org/showthread.php?t=145068")
regards.

---

### Post by dietkinnie on 2006-08-30
Hi There,

Actually i found a way today, however the effects are really slow. I think i have to edit some files to get it to work correctly. If you still dont know how to configure xgl on ur box then contact me. I am intending to write a howtoo for intel cards once i get mine working well. 

//Robert

---

### Post by obi-nine on 2006-08-30
dietkinnie: try removing the blur effect. mine was slow as molasses until I did that. now it's great.

cheers,

obi9

ps. if you stick your howto on a wiki someplace i will help with the docs.

---

### Post by DapperDrakeNewbieDR on 2006-09-02
Thank you folks for your support.

---

### Post by obi-nine on 2006-09-02
Hi folks,

I've put together an installation guide for Aiglx on i915 chipsets over on the Compiz wiki.

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

Please feel free to add or edit.

eg. I would like to know how to switch smoothly between Compiz and kwin. Right now I can always drop back to kwin but then I can't switch back to kwin. If anyone has any useful scripts please add them to the wiki page.

cheers,

obi9

---

### Post by dietkinnie on 2006-09-10
Hi obi-nine! 

Thanks for this how-to "
http://wiki.compiz.net/index.php/Aig...915_video_card". It worked perfectly on my Intel 945GM video card. I disables the blur effect too and it worked perfectly. 

Thanks again !!

Robert.

---

### Post by iLoVe.cF- on 2006-09-10
ehh.. can u guys tell me what u guys get in glxgears -printfps in terminal ?
i get 650.. :s what kind of graphic drivers do u guys use and where is the how to install them.. it is unusable with the settings i have now :'(

---

### Post by obi-nine on 2006-09-11
Actually glxgears crashes out right away telling me:

[B]libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted[/B]

But Compiz works great (with blur turned off). 

Good luck,

obi-nine

PS. I'm running a 2GhZ Pentium M with 1 gig of RAM and an i915 graphics chipset, using the instructions for installing Compiz/AIGLX from the Compiz wiki (above).

---

### Post by mrojas73 on 2006-09-17
> **obi-nine said:**
> Actually glxgears crashes out right away telling me:

[B]libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted[/B]

But Compiz works great (with blur turned off). 

Good luck,

obi-nine

PS. I'm running a 2GhZ Pentium M with 1 gig of RAM and an i915 graphics chipset, using the instructions for installing Compiz/AIGLX from the Compiz wiki (above).


I get the same error on this Acer Aspire 5601 AWLMI but compiz works good.  It would be nice to fix that though!

---

### Post by Kabir on 2006-09-25
The same with Dell Latitude D400.

mixxx: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.

The Xgl is ok but other apps like Mixxx crashes with the same error. Actualy the most people have problem with their soundcards with Mixxx but my issue is with the video rendering..., and I can't even post this like a problem in mixxx forum, because it doesn't concern the program.](*,)

---

### Post by ijanos on 2006-09-27
[Known bug](https://bugs.freedesktop.org/show_bug.cgi?id=8010). Fixed in CVS. Maybe somebody will create a package.

---

