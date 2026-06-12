---
title: "Power Management"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by appye on 2007-11-20
compaq c571nr laptop.

From a fresh boot, all works correctly.  When the laptop resumes from hibernation, all acpi events seem to be disabled until I close and reopen the lid (at least that is what it seems like to me given my limited understanding).  Meaning that once resumed from hibernation, and then sitting idle for the correct period of time, the laptop does not go back into hibernation like it is supposed to.  Nor does it hibernate when I close the lid the FIRST time.  After closing and reopening the lid the FIRST time, it works correctly again, meaning that it hibernates after the correct amount of time, when the lid is closed, etc.  Once resumed from hibernation again, the cycle starts all over again.  Curiously, it always correctly hibernates when the battery gets to the specified (about to die) level.

Also please note that manually initiating hibernation always works fine, regardless of what "state" the machine is in.

I have been having this problem for a while with this laptop and I think I may be able to figure something out with your help.  So far, when I have KUBUNTU 7.10 running on it, I do not have the problem.  I do have this problem when running UBUNTU 7.04 (feisty) and 7.10 (gutsy).  Currently, I am running DEBIAN (testing branch, fully updated), and the problem exists.  In ALL CASES using gnome-centric distros, the problem does not exist for the first day or two that I have it, so I get my hopes up thinking that the problem is solved and then KABLOOEY.  This time around, the problem seemed to pop up shortly after adding the DRI (Mode 0666) section to xorg.conf, rebooting and installing Google Earth.  Basically, I am figuring that this is a GNOME power management issue, because I never did have the problem in KDE when running KUBUNTU 7.10, but I do have the problem with all GNOME distros.

One workaround that I can think of to alleviate this would be to somehow simulate a lid close/open event a minute or so after resume from hibernation, but I don't know how to do this.  I know how to script things at resume, but I don't know exactly WHAT to script!  Any ideas?

---

