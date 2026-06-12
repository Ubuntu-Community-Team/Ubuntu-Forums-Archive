---
title: "ThinkPad T500 Issues and Working"
date: 2009-03-02
forum: Hardware
---

### Post by mperry on 2009-03-02
The thinkpad t500 is a nice laptop and I have about 95% figured out after a shambles of an install which required chrooting, adding a kernel that never did work, rebooting a few times. I'm running the 32 bit version of ubuntu 8.10 on it at this point and it seems like the following things work pretty well:

acpi events - seem to work and I get suspends and hibernations working great now.

wired ethernet - always just works. no big surprises

sound - works across suspend events. imagine that :)

Now for a few things in the "need work" department:

wireless - this always seem to either need work or work different or not obey basic use cases. I can get the wifi back with no big steps after a suspend event part of the time. Other times, I have to manually remove and re-insert the kernel module. The little light thing never does work now with the atheros drivers that I self-compiled. 

Screen resolution - this is a weird and wacky thing. I got some strange resolution first off and now I have it working. Sometimes with a reboot it forgets what its supposed to be.

If anyone has a fix for the wifi, where it stays around after suspend events, let me know :)

---

### Post by Squid Spectre on 2009-03-02
Do you have the issue with the screen brightness constantly resetting itself to mid-bright after coming back from screen saver/suspend/hibernate/restart? Thats driving me insane...

As for the wifi issue, I was lead to believe it is some sort of daemon that was halted when you go to hibernation/suspend but never was restarted when it came back. Though I never dug it to it much because it hasn't been a real big issue for me. (Happened like once out of several weeks of use.)

Also (and this is totally a side note) do you tink you could post your lshw? Maybe the difference between you issue and mine IS the wireless card installed/detected. If nothing else I'd like to see the output from another T500.

---

### Post by mperry on 2009-03-03
Yeah, I have the issue with the screen display thing. I have not been able to find a way to deal with it at a programmatic level so I either just use the screen brightness thing on the keyboard or use a small shell script to raise the brightness. Seems there should be an acpi event handler script that we could manipulate for this issue. I wonder if the T400 has this issue as well.

The atheros drivers seem to do okay on the wireless front but I don't get the wifi back without removing and reinserting the kernel module most times. 

I'll post the output of lshw tomorrow when I'm at work. None of the issues are showstoppers for me and I would not just "go back" to vista business. Vista is just too painful and I was too glad to get away from it after having the new business laptop for almost a month and traveling internationally with it.

---

