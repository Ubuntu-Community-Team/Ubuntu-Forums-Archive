---
title: "Laptop: Strange Problem with Screen Resolution &amp; Suspend -&gt; Broken ACPI / Buggy BIOS"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by Master One on 2006-12-11
I tried the Kubuntu Edgy Eft livecd on our older Gericom Masterpiece XL notebook, but these problems may occure on other machines with buggy BIOS as well. The relavant data of this laptop are:

- P4-2.52GHz CPU
- 512 MB RAM
- ATI Radeon Mobility M9 (Radeon 9000) with 64 MB
- LCD resolution 1400x1050

The livecd generally runs, but the first thing to notice is, that the correct LCD resolution is not automatically selected. It starts with 1024x768, and as videocard driver is shows "ati". When I choose 1400x1050 manually, the desktop gets all distorted, although I can see the correct resolution would have been selected correctly as seen on the mouse cursor, which can be moved from one corner to another without problem. I tried it with the videodrivers ati, radeon (flgrx) and radeon (flrx) proprietary, and all show the same problem. The highest resolution, I can select without getting these distortions is 1280x1024.

I assume it has something to to with the AGP Aperture Size reported wrongly by the BIOS, and then the MTRR settings not being correct. I remember to have played around with Gentoo on that notebook a while ago, and had fixed the MTRR settings with a little script on boot, then I could use the correct display resolution 1400x1050 just fine.

Anybody ever heard of such a problem with (K)ubuntu before?
Any easy fix around?

The other problem with this notebook is connected to ACPI and/or a buggy BIOS. I tried Suspend-to-RAM (which indeed works using the livecd, I can successfully put my ThinkPad T42p to sleep using the livecd, and it awakes just fine), which puts the laptop to sleep (the Suspend-LED goes on), but it does not wake up any more. When I press the power-button to wake it up again, I can see the Power-LED and HDD-LED go on, but no screen, and nothing happens (looks like the system freezes on wakeup, because I can hear the CPU fan getting louder). Suspend & Wakeup works just fine in WinXP, but I remember, I also never got it to work using Gentoo on that machine in former times (I also remember, that in Gentoo playing around with the acpi-daemon, I discovered, that the power-state, so on-battery and on-powersupply, was not correctly reported, which made it impossible to let the notebook react on power-state-change). This surely has to to with broken ACPI / Buggy BIOS.

Anybody knows how to fix this in (K)ubuntu?

I think a lot of people have problems with their laptop not recovering from suspend / hibernation, which always has something to do with a broken ACPI in some way. I remember a thread on the Gentoo forums about how to fix common ACPI problems (DSDT, ECDT, etc.), but I didn't take a closer look at that time. The relevant info can be found [here](http://forums.gentoo.org/viewtopic-t-122145.html).

Any hints are welcome (it's my wife's laptop, and I really want to free it from WinXP, but it would be a pain in the arse, if it didn't work with the full LCD resolution and suspend/hibernation).

---

### Post by drphilngood on 2006-12-11
> **Master One said:**
> ...I assume it has something to to with the AGP Aperture Size reported wrongly by the BIOS, and then the MTRR settings not being correct. I remember to have played around with Gentoo on that notebook a while ago, and had fixed the MTRR settings with a little script on boot, then I could use the correct display resolution 1400x1050 just fine.

Anybody ever heard of such a problem with (K)ubuntu before?
Any easy fix around?

I don´t know of anything to help until you install but after installing you could try this:

[HOWTO: ATI fglrx MTRR error fix]("http://ubuntuforums.org/showthread.php?t=115104")

I´m not familiar with your notebook but you may find this helpful:

[Problem_with_display_remaining_black_after_resume]("http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume")

In addition, you could also try a program like Suspend2.

---

### Post by Master One on 2006-12-12
> **drphilngood said:**
> I don´t know of anything to help until you install but after installing you could try this:[HOWTO: ATI fglrx MTRR error fix]("http://ubuntuforums.org/showthread.php?t=115104")
Yes, that's exactly what I was looking for. It's a workaround, but it should do the job.
> **drphilngood said:**
> I´m not familiar with your notebook but you may find this helpful:
[Problem_with_display_remaining_black_after_resume]("http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume")In addition, you could also try a program like Suspend2.
Not quite sure on that one, the link to ThinkWiki only deals with ThinkPads, and my ThinkPad T42p just works out of the box. With this Gericom laptop it's definitely something different, because appending the acpi_sleep to the kernel line also did not work in my experiments with Gentoo in former times. Another indication is, that the Gericom laptop really locks up, so no Ctrl-Alt-Del, but only the power button remains.

I'm really wondering, if ppl who had that phenomenon on their machines, and it definitely leads to buggy ACPI BIOS implementation, ever got this issue fixed somehow. As mentioned, I've read a lot about such a problem, and it is quite commonly spread all over the different manufacturers, so it really doesn't matter which hardware was implemented in such a laptop, but it all comes down to a buggy BIOS. I am not really a professional, just a user, so I would appreciate some comments concerning the info given by the provided link to the Gentoo forum thread about fixing common ACPI problems.

---

### Post by Master One on 2006-12-14
Ok, I got a little further now (well, I don't really have much time to play around with my wife's laptop, and because she needs her working environment, I'm still doing my tests with the livecd).

The display issue was not a MTRR problem. In fact, it was all recognized correctly except the monitor settings. For some reason "PnP Monitor" gives completely false hsync range, which caused the described distortions, when moving the resolution up. Even the generic settings for "Flatpanel 1400x1050" caused the mentioned problems, because it sets hsync to 90, which obviously is not enough for that panel with that resolutuin @ 60 Hz (looks like it need a little above 90, i guess something between 90 and 91,5). Selecting the generic monitor "1600x1200@76" and setting the resolution to 1400x1050@60 finally fixed the display issue.

The other thing about suspend is indeed an issue with a broken DSDT. I starting reading the mentioned thread in the Gentoo forum, and next move is to decompile & recompile the DSDT with the Intel IASL compiler. I am quite confident that it will show some nasty errors, which need to be fixed to get ACPI fully working on that machine.

---

