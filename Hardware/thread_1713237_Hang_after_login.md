---
title: "Hang after login"
date: 2011-03-23
forum: Hardware
---

### Post by vromanowski on 2011-03-23
When ubuntu boots up on my laptop, after I login @ the password prompt, it hangs on the background for ~20-30 seconds before gnome and everything finally shows up.

I've Googled this and found that other people with this problem were able to fix it by disabling their floppy in the bios, since newer laptops don't have floppys, this was causing the hang in their circumstance, however my laptop's bios has no floppy setting. It does have a few "legacy" settings, but tinkering with those didn't fix the problem either.

I've also tried disabling most startup items, and reinstalling ubuntu, both to no avail. 

Am hoping anyone has any other suggestions I can try. Ubuntu runs fine after it finally does login but it's just an extreme annoyance :D

laptop specs:
core i5 460M @ 2.5 ghz
nvidia 310m (drivers installed)
4gb ddr3 1066

---

### Post by Dark_Stang on 2011-03-23
What you'll want to do is profile your boot process. When I worked for Geek Squad we had awesome tools that would do this for us on Windows. But I've never played with any boot profilers on Linux. There is an application called "BootChart" that claims to do it though, so that is where I'd start.

---

