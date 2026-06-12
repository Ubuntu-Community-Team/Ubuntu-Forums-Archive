---
title: "How do I switch ACPI to APM?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by x22304 on 2007-10-21
Hey guys,

I'm an absolute beginner to Ubuntu, actually to anything Linux. First, I'm a Windows/Macintosh user. For home I use Windows, it came pre-installed, I have all the disks, it's worked (with it's Windows frustrations) and finally, like Windows, it crashed. I lost a bunch of stuff that I wasn't able to back-up in time. Now, on top of all that, I have the famous "Windows hangs with 34 minutes left on install." So overall, it fed my hatred to Windows enough that I finally made the switch to Linux.

At work, I use a Macintosh, I've never had problems with it. In fact, I absolutely love it, however, I can't buy one for home because of the Macintosh issue. You know, the one where they cost too ****ing much money.

Anyway, I got Ubuntu up and running but I am having a few issues.
 Let's start with my computer's basic specs.

Make: Enpower (Laptop)
CPU: AMD Athlon 3200+ 64
RAM: 512 Megs
Video: ATI Mobility Radeon 9700 

Now, being a complete newb to Linux, I'm a bit lost, not too much, but a bit. This is what is happening. First, after install, my computer wouldn't even boot, it hung with about five black boxes left to fill with orange on the boot bar. After research it seemed it was ACPI so in pre-boot I typed ACPI=off; it worked, I booted in fine and started loving Ubuntu; until restart. I had to do it again.

After looking around, I found this thread ([http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620)) I followed what it said and my computer boots fine every time now. Still a few issues though. I don't think APM started up successfully so in my Kernal I added AMP=on. Still nothing, battery still doesn't work, it just says it's running off battery power even if it's plugged in, it also is always reading that it is at 0% even when it's had time for a full recharge. This is one of my only two frustrations (so far).

The second one is if my computer goes to sleep after the screen saver has been going for a bit, it wont come back on. All the lights are lit, but just a black screen. Also if I close the lid, it will not come back on either. So that is pretty frustrating.

Any other alternatives on what this may be? I'm not even sure this is an ACPI or APM issue, since I'm pretty new, I am just assuming that is the problem because off the pre-boot ACPI=off; therefore I have been following that as the issue.

Thanks in advance for reading and responding to this long-winded post.

---

### Post by x22304 on 2007-10-22
Well, I've still been trying to work on this, seems I'm totally lost. However, I've been learning other stuff, Ubuntu is looking pretty good so far, I just need that battery to show how much life is left. After I run my computer for two hours I just plug it in cause Windows used to run for two and a half so I figure it's probalby getting low; I don't want to suddenly loose a bunch of stuff.

I'm still curious to find out if anyone knows why AMP wont activate after switching ACPI=off. Any comments to this would be greatly appreciated.

---

