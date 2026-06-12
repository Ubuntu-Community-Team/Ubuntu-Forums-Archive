---
title: "automatic hibernations"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by monoufo on 2007-10-20
I can manually hibernate the computer just fine.  It's a thinkpad r51.  However, for the past several weeks, it hasn't been hibernating on its own.  Gutsy is final now.  I'm going to give it a fresh install after mac4lin 0.3 is released because I'm experiencing lots of odd problems.  But in the meantime, it would be cool if someone knew how to fix this.  the battery gets low and it should hibernate itself.

---

### Post by 5-HT on 2007-10-20
System -> Preferences -> Power Management
cheers,

---

### Post by monoufo on 2007-10-20
I thought it was implied that I already had it set in there.  It's not working.

---

### Post by 5-HT on 2007-10-20
> **monoufo said:**
> I thought it was implied that I already had it set in there. It's not working.
No.  You didn't even specify whether you were using gnome nor how you manually hibernate (pm-utils, tux-on-ice/suspend2, acpi, etc...).

pm-utils via hal interaction now handles suspend-to-disk/ram and has become the new ubuntu standard. Are you calling pm-utils to manually hibernate, or doing it a different way? Check out the pm-utils logs and the kernel logs both when manually hibernating and when hal should automagically hibernate based on battery life remaining. Other things to consider would be group membership for hal and proper gconf settings to let pm-utils do its magic when automatically called, in addition to a proper config for pm-utils.

Another thing to consider is that pm-utils is new in Gutsy and you mentioned that you were also experiencing other issues. It's possible that the new suspend-to-disk/hibernate architecture hasn't been fully and properly implemented on your system.

Sorry, but that's as far as I go with this-- I do not appreciate the smartass attitude when I'm only trying to help and you haven't even bothered to include proper diagnostics in your post even as a follow-up. My first post was simply an initial guess as without potential dist-upgrade issues, it's the only thing the user *should* need to do. When you throw in a dist-upgrade that may not have gone totally as intended--exemplified by the other apparent ''odd issues" you referred to--it's a whole new kettle of fish. While it can definately be solved, the solution would be more involved and there are no diagnostics that you have provided to go on.

cheers,

---

### Post by monoufo on 2007-10-21
I don't know what it's using to hibernate.  I juck click the hibernate button in the quit menu.  Sometimes i hit Fn+F12 and that does the same thing.  Gnome is implied.  If I wasn't using gnome, I'd mention it.  If you had better reading comprehension skills, you'd be able to tell that i have been running Gutsy for at least several weeks (actually since tribe 5), and that hibernation was working properly on its own previously.  That means it must have been set properly, or else I wouldn't be expecting it to work.

if I'm using the computer, I'd probably plug it in before it gets to the hibernation part.  I want it to turn off on it's own when i left it unattended.  I don't have the computer sleep unless I close the lid, because it interfers with bit torrent.  So I might leave the computer around, fully awake downloading and uploading.  It might lose power due to someone unpluggin it, or the loose connector.  Sometime later, it should hibernate itself.

you tell me to check all kinds of permissions and whatnot.  my question is who changed them?  you asked me to do way too much work for a minor thing.  I'm going to do a fresh install soon anyways like i originally planned on doing. who knows what i hosed up since tribe 5.  although awn is going to be a pain in the *** to install and reconfigure. It has a zillion dependencies.

---

