---
title: "Any Good HDD Comprehensive Test Programs?"
date: 2015-04-08
forum: Hardware
---

### Post by 56es8lTI on 2015-04-08
I have a suspicious HDD in one of the boxes I'm converting over to Lubuntu/LXLE.  Some rudimentary tests indicate that it's supposedly fine, **but** it's showing install and boot problems that are **not** shared when I use a different HDD.

Any thoughts on this?

As always, thanks for any useful advice!

---

### Post by TheFu on 2015-04-08
If you've already isolated the controller and cable, know those are not the issue, then smartctl is really the only tool. Because SMART data isn't very good without watching it over time, it is of limited use. By the time SMART reports an issue, it is too late.  Watch the counts weekly to spot trends. 

For a failing disk, perhaps a tool like badblocks (can be called by fsck with certain options) would be useful?

---

### Post by weatherman2 on 2015-04-08
I disagree with TheFu.  I have found S.M.A.R.T. information very useful on many hard drives.  Although I don't rely on S.M.A.R.T. data to predict a hard drive issue, it is very useful to determine a drive's current state.

You can also run built-in diagnostic tests with S.M.A.R.T., using the drive's own controller.  In Linux, you can use GSmartControl (install it if need be on a live boot USB) to check current S.M.A.R.T. Attributes.  GSmartControl is a graphical interface for smartmontools (which can also be run in a terminal with the smartctl command).  In GSmartControl, look at the Attributes tab and see if any are highlighted in pink - these are likely problems (not always - depends on the attribute).  Some attributes marked "pre-failure" are not in fact failing - that's just the type of attribute it is.

You can also run S.M.A.R.T. tests with GSmartControl.  I'd recommend running the Extended Test (can take a long time if the drive is large).  Run the short test first, because that completes quickly and will generally fail immediately with a drive that is in bad shape.  Then you know it's probably bad.

---

