---
title: "Ubuntu on Dell XPS M140 and Overheating"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by feveryear on 2006-10-05
I've been browsing the forums for quite a while. I've put Ubuntu 5 on my Desktop when it came out, and starting in Computer Science at college has gotten me interested in Ubuntu 6. I put it on my XPS M140, and have loved it, until recently when I found out the the fans aren't cutting on so it may be bad, as in overheating. Well, from what I've learned about processors, at least Pentiums, they have the function of shutting down, as a safety feature, before overheating. Now, I never really focused on trying to notice the fans running, but my laptop's never shutdown before. You'd think if it would overheat, it would shutdown, or at least freeze, then you'd know the fans weren't cutting on or working properly, correct? I love linux, and I want to use Ubuntu. I know nothing about any other linux, which is why I want to stick with Ubuntu. I haven't experienced overheating yet, but I'll look for it, in the mean time, isn't it safe to say that the computer will shutdown/freeze if it does start to get too hot?

---

### Post by Frogger on 2006-10-07
Yes, it is safe to say that at the very least your computer would become unstable if it began to overheat.  If you still have the windows partition on it, then I'd recommend downloading cpu burn-in (just do a google search) and time how long it takes for the fans to cut on, the do the same under linux and if there is a major difference then post again.
I do not think it is likely (but it is not impossible) that Ubuntu is causing your fans to not turn on, I think they are controlled via the BIOS.
Two, I have read that those systems have a tendancy to get rather hot even when running Windows.

ALSO: RUN BURN-IN WITH ERROR CHECKING- just in case, so that if your system begins to overheat, burn-in will stop.

---

### Post by gn2 on 2006-10-08
Have you tried loading the sensors-applet?

It's possible to display the running temps on your panel, so you can keep an eye on it.

---

### Post by feveryear on 2006-10-08
I'll have to check out that program. I've noticed it's gotten hot with Windows sometimes also. So just see how long it takes from boot up in each OS til the fans come on? I'll have to try it. Thanks guys. I really want to run ubuntu on my Dell. I just don't want it to fry it.

---

### Post by feveryear on 2006-10-08
I installed Ubuntu, and I've had my hand up against the fan for a while. When it kicks on, you can hear it, if it's quiet. But I get a satisfying hot air blown on my fingers when the fan kicks on. The fans do seem to work. I don't think they'd only work partially and sometimes not work. They are blowing the air out. My laptop's always been warm, even with XP. I think that's just how Dell made them. But the fans appear to be working well with me

---

### Post by rancourt on 2006-10-09
I'm running Dapper on my Dell XPS M140, and the fans are definitely working for me -- they kick in on rare occasion, and I can indeed feel the hot air exodus from the side. I noticed I was running hotter at first, too -- I'm not sure which change did the trick, but after upgrading to 2.16.15-27 686 kernel and switching processor scaling to 'OnDemand,' I've had no issues. I hope this helps you.

---

