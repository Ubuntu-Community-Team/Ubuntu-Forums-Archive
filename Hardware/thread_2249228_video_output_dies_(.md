---
title: "video output dies :("
date: 2014-10-20
forum: Hardware
---

### Post by osakechan on 2014-10-20
I've been running 12.04 LTS for some time now, and haven't made any hardware changes to my system in at least a year or two.  I haven't installed any updates for a week or two.I booted up today and after a few minutes I stopped receiving output from my video card.  It appears my system continued running as usual so I am reasonably certain this is an issue with my GPU.  I immediately performed a hard reboot, but the video output remained dead.  After leaving my system shutdown for a couple minutes I tried again.  This time video worked but then stopped again part way through the boot.  I'm wondering if perhaps this is an overheating issue (maybe the GPU fan is starting to fail?).  I'll go buy a can of air to see if i can blow it out, but could it be some other type of hardware failure?  I know there is a good chance ubuntu is logging this failure somewhere.  Suggestions on how to check?  Thanks!

---

### Post by weatherman2 on 2014-10-20
Yes, overheating seems a likely culprit.  Open the computer and make sure the fans are working.  And make sure the heat sinks the fans are (probably) attached to are not clogged with dirt and dust.  If so, clean them out.  Sometimes you may need to take fans or heat sinks off to clean them properly.  If cleaning a CPU heat sink, it's usually a good idea to clean the surfaces and re-apply new thermal paste.

A failing power supply is also a possibility.

---

### Post by WinEunuchs2Unix on 2014-10-20
The "video output" is to the "built-in display" of a "laptop" or an "external display" of a "laptop" or "desktop".  If a laptop and it is at room temperature then it wouldn't overheat for awhile.  If a laptop with broken fan you can sometimes go into BIOS and switch the mode from "auto" to "low speed" (ie 1 Ghz when the max is 2 Ghz) and it will run without a fan albeit slower.

Sorry to say "video output" is rather vague.

---

