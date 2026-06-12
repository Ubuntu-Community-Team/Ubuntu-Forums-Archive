---
title: "Hardy freezes while typing on LG LW60"
date: 2008-04-26
forum: Hardware
---

### Post by crazy_robots on 2008-04-26
Hi!

I have some unusual (for me) problem with my newly-installed Ubuntu Hardy. It freeze randomly while I typing in pidgin, gedit, etc (in fact, i had no problems with typing url in firefox, but page search freezed the system after the 2nd letter =) ) There is a 100% way to freeze the system also: use autocompletion in console with no difference if it is graphic or not. I hear the typical head-parking sound in hdd and that's it - no response of any kind.
It's all happening on LG lW60 laptop (P-M1.6, AtiX600m, Seagate 5400.3 100Gb)
Slax 5.04b and Knoppix3.3 worked fine (just pcmcia detection trouble which is easily solvable) and WinXP is also have no troubles of such a kind.
System works fine if i don't touch keyboard, but i have no reason to convert my laptop into the server =) 

If anybody knows what kind of poltergeist I have, I will be very thankful :) And sorry for my english if anything's wrong :)

---

### Post by hjtrakfo on 2008-04-27
I have the same problem on my LW60.
Seems like it happens when the shell tries to send a beep (like in autocompletion with choices).
So it might be audio driver related. I'd appreciate a pointer to a solution too. I would be happy disabling audio altogether, I never use it.

---

### Post by crazy_robots on 2008-04-27
Thanks a lot =)
This seems to be the root of the problem: after disabling the system beep (switching it to a graphics mode) autocompletion just blinks the window - not freezing the system. =) This is done by System->Parameters->Sound->System Beep.

P.S.
Ubuntu and LW60 sound card has a strange friendship generally - i'll probably have to dig more this theme later...

---

### Post by hjtrakfo on 2008-04-27
Thank you for the way to disable the beep.
When you find a more general solution please remember to post the how-to!

---

