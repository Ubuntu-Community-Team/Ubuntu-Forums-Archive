---
title: "Karmic on Dell Mini 12"
date: 2009-11-02
forum: Hardware
---

### Post by Michael%S on 2009-11-02
(This is a direct continuation of this thread: [http://ubuntuforums.org/showthread.php?t=1294173](http://ubuntuforums.org/showthread.php?t=1294173) )
Has anyone discovered anything new about controlling brightness in Karmic?

If you have installed Karmic on a Dell Mini 12, how has it been working for you? Have you had the same difficulties described in the old thread(s)? Please share your experience!

---

### Post by michael37 on 2009-12-23
Just to fill in the details. I installed i386 today and noticed that brightness keys work just fine in i386.  Seems to be lpia problem.  This problem is probably irrelevant since lpia is discontinued with lucid.

But not everything in i386 is working well.  I am now having problems with audio driver.  With lpia,
options snd-hda-intel model=dell in /etc/modprobe.d/alsa-base.conf fixed snd-hda-intel problems, but with i386 it does not.  My dmesg is full of error messages hda-intel: spurious response 0x0:0x0, last cmd=0x370600 and sound stops working soon after reboot.

Dell Mini 12, quadruple boot
- Windows 7
- Karmic 9.10 LPIA
- Karmic 9.10 i386
- Jolicloud Pre-Beta

---

### Post by mocoloco on 2009-12-30
Installed it on my wife's mini 12.  Thanks a ton to michael37, lucazade and the others for the scripts and instructions to get the poulsbo driver working.  Same issue of lack of brightness changes but not a big deal.  Initially there was a problem with the cursor disappearing after wake up from susupend.  Oddly (but happily) it's gone away after some updates, not sure why as they were for gstreamer and apparmor but won't complain :).

I know they don't sell it anymore and don't support anything past Hardy, but it seems to me Dell should be hosting these types of things in the community/wiki pages.  Would be a way to show they care, but still be able to say "supported by the community, not directly by Dell".

---

### Post by michael37 on 2009-12-30
> **mocoloco said:**
> Installed it on my wife's mini 12.  Thanks a ton to michael37, lucazade and the others for the scripts and instructions to get the poulsbo driver working.  Same issue of lack of brightness changes but not a big deal.  Initially there was a problem with the cursor disappearing after wake up from susupend.  Oddly (but happily) it's gone away after some updates, not sure why as they were for gstreamer and apparmor but won't complain :).

I know they don't sell it anymore and don't support anything past Hardy, but it seems to me Dell should be hosting these types of things in the community/wiki pages.  Would be a way to show they care, but still be able to say "supported by the community, not directly by Dell".

Dell Mini 12 is nearly as capable as "small and light for the road warrior" ultra-portable Dell Vostro 1220, for one third of Vostro price.  Still wonder why Dell doesn't make Dell Mini 12 anymore?

---

### Post by sol1tude on 2010-01-05
I think [http://ubuntuforums.org/showthread.php?p=8612908#post8612908](http://ubuntuforums.org/showthread.php?p=8612908#post8612908) will help you with your brightness.

---

### Post by mocoloco on 2010-01-12
Got brightness working, all was good.  Then my wife got updates, including a kernel update, and that broke the graphics driver :(.  She can still boot the previous kernel.  I haven't had a chance to look at it yet, but I'm assuming I'll need to reaload the driver because it's kernel specific, correct?

---

### Post by jbernardo on 2010-01-13
> **mocoloco said:**
> Got brightness working, all was good.  Then my wife got updates, including a kernel update, and that broke the graphics driver :(.  She can still boot the previous kernel.  I haven't had a chance to look at it yet, but I'm assuming I'll need to reaload the driver because it's kernel specific, correct?

Typically, you'll have to boot into recovery mode, and do "dpkg-reconfigure psb-kernel-source". That should reinstall the kernel for you.

---

### Post by mocoloco on 2010-01-14
> **jbernardo said:**
> Typically, you'll have to boot into recovery mode, and do "dpkg-reconfigure psb-kernel-source". That should reinstall the kernel for you.

That did it, thanks.

---

