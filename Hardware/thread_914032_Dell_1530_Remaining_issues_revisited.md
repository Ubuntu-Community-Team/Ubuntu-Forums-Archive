---
title: "Dell 1530: Remaining issues revisited"
date: 2008-09-08
forum: Hardware
---

### Post by mailforbiz on 2008-09-08
Hi all

I've had the XPS 1530 (Nvidia 8400 GS, Hardy clean install) for about 4 months now and have managed to make most of the essential (for me) features work with Hardy on it. I almost never use the Windoze boot on it anymore. But while a couple really annoying issues are much better than when I started, they still crop up often enough to bother me so thought of checking back here to see if anyone's got a better handle on them. 

They are :
[B]
a. Suspend/hibernate/Sleep 
b. occasional weird graphic issues (text not showing in dialog box)
c. Heat[/B]

a. Resume/Hibernate using the proprietory drivers
=================================================
(The standard drivers DON'T work for Suspend/Resume or Hibernate for me.)
Resume from Suspend works mostly. At least the first 2-3 times. Sometimes, it comes up with a blank screen and then the only recourse is to reboot using the power switch. If the display is put to sleep (like if I leave the laptop on for a long time w/o suspending), sometimes the screen goes blank and then its toast, I need to reboot to get the screen back. I rarely use Hibernate but of the few times I've used it, it worked a few times and other times it gave an error when trying to hibernate and then didn't wake up right. 

b. Weird graphic issues
======================
This really bothers me. It happens with some applications. Like an Eclipse dialog would have no text or buttons. It doesn't happen with the standard drivers, only with the proprietory ones. I haven't really been able to spend time to find the pattern when it has this problem and when it doesn't except it never happened with the standard drivers.

c. Heat
========
The laptop gets a little hot (no intensive apps being used btw) but I can still live with as long as I have suspend which shuts it off after some time. If I leave the laptop overnight for eg, that thing gets freaking hot though. So in short I need to make it sleep. Once I left work in a hurry and closed the lid and shoved it in my backpack. It was burning hot when I got home which was about an hour later (heat dissipation is not too great in my backpack so that was the major reason besides the fact that 1530 is kind of a hot laptop). So now I have set it up to suspend when the lid is down.

Overall, I'm pleased with my lappy and even more pleased that I finally weaned myself off Windoz but it would be great if I can resolve the final few issue that are functionally critical for me. I've had other minor issues but I can live with that (for eg., losing my Bluetooth mouse once in a while). Anyone else has had better luck with the above though?

Thanks in advance,
HT

---

### Post by mailforbiz on 2009-01-31
Its kind of late for this thread, but just in case this might help someone reading the thread in future:

The heat and suspend/resume issue has been mitigated somewhat by upgrading to Intrepid.
The problems related to text not showing up in graphics were resolved by updating to new GTK libraries - libgtk2 and libwxgtk2.8.

---

