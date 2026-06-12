---
title: "Catalyst 11.5 on Hybrid Graphics"
date: 2011-06-15
forum: Hardware
---

### Post by vedovatti on 2011-06-15
Hi there,

I have an HP touchsmart tm2 with hybrid graphics Intel/ATI.

I read on the released notes of the property driver that since the catalyst 11.4 the switching between cards is supported in Linux.

I am afraid to try it because when I did it with Ubuntu 10.04 and I never saw my system after installing the property drivers. And I had to reinstall the whole system.

Does anybody have tried the new catalyst 11.5 (property driver for ATI) in a laptop with hybrid graphic cards?

Thanks

---

### Post by madik on 2011-06-15
I've tried it but it doesnt work for me too. My classic gnome running in 2D and attempts to run some 3d applications are failing.
I have Lenovo E420 with Sandy bridge graphics and switchable AMD HD6630M. 
When i installed AMD/ATI proprietary graphics drivers from the "Additional Drivers" menu there was Catalyst control center shortcut in System/Preferences but it wasnt working and was showing only some error message. 
When i then installed Catalyst 11.5 from AMD website directly from terminal and "Sudo sh ati-driver-installer-11-5-x86.x86_64.run" command it worked out pretty much the same and 3D doesnt work. But the Catalyst shortcut in System/Preferences is missing this time.

Would be really nice to have this working in Ubuntu as it works in Windows..

---

### Post by not4us on 2011-06-15
I also have a Lenovo Edge E420 with switchable ATI 6630 / Intel HD 3000 (sandy bridge graphics) and Natty recognizes the ATI card but when I install the proprietary Catalyst drivers to get the switching working I get a message saying that no ATI hardware is  detected and it throws me back to Ubuntu "Classic".
I believe the problem is that this model relies on a "software" switch - no BIOS or hardware switch - and Ubuntu picks the Intel discrete graphics before the ATI dedicated one.
My laptop is currently being repaired under warranty for an unrelated issue but once I get ti back next week I'll do some further testing to see if we can get the Radeon card working.

---

### Post by vedovatti on 2011-07-07
Hi!
I have good news. I just installed the Catalyst 11.6 on my HP touchsmart tm2 with hybrid graphic (switchable graphics) and surprisingly it works.
I have a ATI HD Radeon 5450 and Intel integrated graphics i5. It changes without problem between cards (although you have to restart the system). But resume/hibernate/logout/shutdown work well.

The only problem is that when I change to intel it doesn't activate the 3D acceleration. So Ubuntu start in Unity 2d. A pity. Just wanted to let you know. It is the first time I see that a company supports in Linux (switchable graphics driver ATI/Intel) a driver and not in Windows.

Bye

---

### Post by vedovatti on 2011-07-07
I just found out that it has two big bugs. The one that the Intel graphics are not 3D accelerated and that on full-screen video, games and video-out don’t work. It freezes the system. So... maybe on the next releases. We could have more luck.

---

