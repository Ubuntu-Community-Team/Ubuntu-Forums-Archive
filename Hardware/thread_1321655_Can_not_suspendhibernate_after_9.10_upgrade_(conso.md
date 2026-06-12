---
title: "Can not suspend/hibernate after 9.10 upgrade (console suspend works)"
date: 2009-11-10
forum: Hardware
---

### Post by jtp755 on 2009-11-10
Ive looked around a bit and cant find anything recent on this so here goes.

Before i upgraded to 9.10 i could suspend using the hot key on my keyboard, i could not how ever use the hibernate hot key. I could also use the suspend AND hibernate buttons on the K menu and both worked fine.

After the upgrade i can no longer use the hot keys or the buttons on the K menu to suspend or hibernate. I did find out that if i go to console only mode from KDM that i can use the suspend hot key and it worked great. When i press the hot keys or use the buttons a pop-up in the lower right-hand screen tells me that Power Management - Screen is being locked. That is all it does is lock the screen. I checked all my settings in System Settings - Power Management and nothing is set to lock the screen. They are set to Suspend to RAM.

Amidst searching yesterday i found out that because i did an "upgrade" Grub did not get upgraded so i did that and it didn't help either.


Specs:
Dell E1505 laptop
KDE 4.3.2
Kubuntu 9.10
Power Management Backend - HAL-Power
Kernel - 2.6.31-14-generic
RAM - 2 GB
Swap - 2 GB
Grub2 (grub-pc)


Any ideas?

---

### Post by jtp755 on 2009-11-10
This has been solved.

I tracked down some other log files i ran across during some posts i was reading.

/var/log/pm-suspend.log gave showed me that the suspend was being "inhibited."

Looking above that line in the log file it could not find the pacmd command for PulseAudio. I was missing the pulseaudio-utils package. I installed it and tried suspending and voila! I tested hibernating as well from the K menu and it works.


Now to get my hibernate hot key working!

---

### Post by paulchinnz on 2009-11-23
Unfortunately still a problem for me. Also using a similarly spec'd Inspiron. Any ideas?

---

### Post by jtp755 on 2009-11-23
Are you using KDE or GNOME?

If KDE...go to System Settings -> Advanced tab -> Power Management and check to see if PowerDevil is controlling the power. Go through the settings in there and make sure things are as they should be.

Did you check the log file i mentioned? Can you post the last part of it here? Can you give any more details on what you have looked into/tried and what exactly your problem is?

---

### Post by paulchinnz on 2009-11-23
Sorry should have been more specific. Running GNOME, have checked /var/log/pm-suspend.log and everything is either 'success' or 'not applicable'. The problem with my hibernation attempts from the logs appears to be that it tries to hibernate but within a minute or so something tells it to wake up and thaw.

---

### Post by jtp755 on 2009-11-23
Hmm..

Not too sure. Have you checked dmesg and/or /var/log/kernel after you try to hibernate?

Do you know what power manager is being used or what suspend/hibernation application?

Does your system suspend and NOT hibernate or does neither work?

Ill try to help you work through it but im just guessing..

---

### Post by paulchinnz on 2009-11-24
Bizarre... started working again. Will let you know if not. Didn't know about dmesg before so another useful tool in my terminal toolbox. Thanks.

---

