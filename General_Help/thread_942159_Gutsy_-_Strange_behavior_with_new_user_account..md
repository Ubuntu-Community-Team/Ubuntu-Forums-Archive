---
title: "Gutsy - Strange behavior with new user account."
date: 2008-10-08
forum: General Help
---

### Post by Vryko Lakas on 2008-10-08
This is weird. I've had Gutsy Gibbon as the sole OS on our family computer for just over six months now. Initially I had set up four users for the household. 
Recently I had to create a new user account  and since then I've been getting weird errors. 

-When all five users are currently logged in and I try to switch users, it'll tell me "Flexible X blah blah reached allowed limit" and I'll have to log out of the account to switch users. I found there's a bug report filed for this already, but it hasn't been prioritized and there's no fix yet. The only forum thread about this error is an unanswered one in the archives. 

-Twice now I've tried to switch users and been kicked to the command line interface. Rebooting seems to work the first time, but when I had to rebooted just now it took several minutes of a blank screen and blinking cursor for the GRUB boot menu to come up. This is odd, because I'm not dual-booting so GRUB never even *shows* a menu on this computer. So I've just become much more uncertain about how long I'll be able to use the family computer reliably. 

The computer has an Nvidia 8400 GS using the proprietary driver. I'm not using Desktop Effects for any of the users, and I even switched all the virtual desktops from 2 to 1 thinking it would free up whatever is causing the problem. So far it doesn't seem to have any effect. 

I -can- upgrade to Hardy, but with Intrepid just around the corner I'd rather hold off and make sure I can set aside a day to do proper backing-up. Since I haven't seen any information about the first error, I figured I'd ask about it. Hopefully somebody can explain what's going on. Even better if there's a way to fix the issue. I want a reliable computer again. :(

---

### Post by pytheas22 on 2008-10-08
If this issue only exists in Gutsy, I doubt that it will ever get fixed, unfortunately.  Your best bet might be just to upgrade to Hardy--in fact if this is a family machine, maybe you just want to go to Hardy and stay there, instead of using Intrepid, since Hardy is supported for the next three years but Intrepid for only have that time.

If you provide a link to the bug report that you found, however, I'll google around and see if anything comes up.  But again, I think that your best bet is going just to be to upgrade.

---

### Post by Vryko Lakas on 2008-10-09
I've been thinking about that. I just feel like I'll miss out on more advanced features with the next release, or a more stable/better configured Compiz, or something else that would make life a bit easier. It bugs me because usually I prefer not to upgrade or reinstall an operating system every six months to a year. 

Anyway, here's the report I found. 
[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/232078]("https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/232078")
I don't know if it's Gutsy-only or not, but that's the only place I've seen it.

---

### Post by pytheas22 on 2008-10-09
Unfortunately, I can't really find anything that would lead to a solution--I can find only the bug report and unanswered forum post that you already mentioned.  My *guess* is that this has been fixed in more recent versions of Ubuntu; otherwise we'd probably see more people complaining about it--I'm sure that you and sierpins are not the only people in the world running Ubuntu machines with several users logged in for long periods of time.

As for the upgrade, I'd recommend that you move up to Hardy and stay there.  If you stay on Gutsy, you won't be able to download software from the repositories or get updates after support ends this spring, but Hardy will remain supported for several more years.  Lack of repositories/updates is the major reason that I would upgrade my Ubuntu system.  Intrepid will contain a few interesting [new features]("http://www.ubuntu.com/testing/intrepid/beta#New%20Features%20since%20Ubuntu%208.04"), but I don't think you're going to be missing out on anything earth-shattering if you stay on Hardy--and Intrepid's end-of-life is before Hardy's anyway.

---

### Post by Vryko Lakas on 2008-10-10
I may just do that after all. 
Of course they make X.org 7.4 sound so very appealing in light of my recent trouble.

---

