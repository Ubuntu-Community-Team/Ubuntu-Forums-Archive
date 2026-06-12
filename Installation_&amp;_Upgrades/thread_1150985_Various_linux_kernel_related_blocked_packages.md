---
title: "Various linux kernel related blocked packages"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by pgratz on 2009-05-06
Hi All,
Just a relatively quick, newbie question.  I recently started using Kubuntu after switching from Gentoo.  Anyways the auto-update tool popped up today and along with a set of normal upgradable packages it also listed a set of kernel package upgrades that are "blocked" but it did not display any further info about why they are blocked or what I should do about it.  Can anyone point me in the right direction to figure out what this means and what I should do about it.
Thanks!
Paul

---

### Post by cariboo on 2009-05-06
Usually if there is an update that is being held back, it means that there are some dependencies missing, give it a couple of days for the dependencies to catch up. 

I'm running Karmic Koala, I've had 6 package awaiting dependencies for about a week, but the build farm has just about caught up so they should be installed any day now.

---

### Post by Scott M. Sanders on 2009-06-06
This seems to affect all the Ubuntu variants (not just Kubuntu), as I just have straight Ubuntu (9.04 Desktop) and came to the forums today seeking an answer to this issue myself. (So an update to this thread's variant spec would be preferable.) 

I should also note that I have Proposed Updates enabled, which is where it's from presently, and that in Update Manager all the blocked updates (all "linux-*") are listed as just 3 KB in size. 

What's most annoying though is that the update icon won't leave my systray until this issue is resolved apparently, maybe because I manually reverted Update Manager's settings to act like 8 did instead (I don't notice the taskbar sometimes), but being perpetually notified of an update that cannot actually be applied is undesirable regardless of notification preference.

---

### Post by shaunehunter on 2009-06-10
this is how to get blocked updates:

from the terminal type.

sudo apt-get dist-upgrade

then your password.

I read somewhere on these (or kubuntuforums.org) that the reason you get these is they require the removal of other packages.

That might be wrong and or misquoted as it was a while ago but it's never led to problems for me.

---

### Post by scearley on 2009-06-11
> **shaunehunter said:**
> this is how to get blocked updates:

from the terminal type.

sudo apt-get dist-upgrade

then your password.

I read somewhere on these (or kubuntuforums.org) that the reason you get these is they require the removal of other packages.

That might be wrong and or misquoted as it was a while ago but it's never led to problems for me.

This did not work for me.

I'm completely unable to upgrade anything at this point.  It shows me everything that needs to update in adept, I go to update (887 packages), and it gives me a non-committal answer that it possibly couldn't download or it possibly breaks packages.  Forcing the download above generates an error message regarding cups-pdf and cancels any download.

If I go to update to 9.04, rather than the simple packages, then it directes me to download all of these packages (even though I've downloaded them multiple times already), runs the install, which simply vanishes.  a few moments later, after I think the installer has just crashed returning no error message, I get an error message just as when I was simply trying to update the individual packages, rather than the just-attempted full upgrade to 9.04.

If it's w/r/t the missing dependencies as cariboo mentions, then I have to ask why his post is dated May 6 and a full month later I'm still waiting for these dependencies.  That's substantially more than a few days.

How do I upgrade to 9.04?  Please don't tell me to use a disk, because somehow the BIOS on the laptop I'm upgrading no longer opens, and I can't change the jumpers to look for a CD player/USB on load.  These only become active after the boot.

---

### Post by Scott M. Sanders on 2009-06-13
Try mounting the (K)ubuntu 9.04 CD in your current (K)ubuntu installation. It should prompt you to upgrade. 

Anyway for me, as cariboo907 said, mine were proposed updates that were waiting on dependencies, and those dependences indeed were fulfilled in the next few days, allowing me to install those updates as all other updates with properly fulfilled dependencies (as through the default -- i.e. not "proposed" -- software channels). 

I dunno that "forcing" updates without fulfilled dependencies would be such a good idea, if that is even possible.

---

