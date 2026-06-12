---
title: "xorg.conf issue"
date: 2009-02-24
forum: Hardware
---

### Post by kwr2k on 2009-02-24
Although I use only kubuntu, it might be applicable to other flavours of ubuntu as well.

Basically my question is simple: Why is xorg.conf so minimal in [k]ubuntu? Also, why can't I change settings in it without the system telling me that it needs to reconfigure my display?

I have a fairly recent laptop - HP 6530b - with Intel GMA chipset and an HP LP2065 external LCD monitor. On openSUSE (which I am currently using), it is a simple task to include the external monitor in a dual-head setup where my desktop spans across both displays.

However, with Kubuntu, I've had no success so far. For instance, dual-monitor requires setting the Virtual resolution to 2400 2400 (in my case) in xorg.conf. However, the moment I add this like to Display section the system forces me to reconfigure X. Needless to add, I am back to the original configuration without the joy of dual monitors!

Why is [k]ubuntu doing things this way? Why can't, if the user requires, xorg.conf be manually edited? If that is not allowed, how do I configure dual-head display?

Although I am using JJ Alpha2, this issue is not limited to Jaunty. I have seen this with Intrepid too.

Please somebody explain and help.

Thanks.

---

### Post by geraldm on 2009-02-25
Use of the file xorg.conf is deprecated. 
Most recent display monitors have the ability to tell the system what their specifications.  The file xorg.conf was used prior to the time when this communication existed, and usually is no longer needed.

When there are two monitors on a system, it may be necessary to declare how the displays are to be used: as separatly, both use the same image, etc.
If you do edit, be sure to back up the file first, so you can restore it if a mess is made.  

I think you received a warning message about the configuration.  Do perform the backup procedures before any continuation.  Perhaps you will not get a reconfigured xserver unless you opt for it.  The message should have presented you with the option ?

Gerald

---

