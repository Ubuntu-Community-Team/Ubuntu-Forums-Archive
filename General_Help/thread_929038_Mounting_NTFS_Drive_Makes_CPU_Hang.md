---
title: "Mounting NTFS Drive Makes CPU Hang"
date: 2008-09-24
forum: General Help
---

### Post by kidko on 2008-09-24
This problem just appeared two days ago, actually. Before that, everything was fine.

However, here's the gist of it: I mount an NTFS drive (for example, /media/myDocuments). After about ten minutes, my CPU usage skyrockets and there's nothing I can do. The little light on my tower (the "working" indicator or whatever it's called) does not turn off or even blink; I can't move my mouse or even CTRL+ALT+F*x* to try to unmount from a non-CPU-heavy environment. All that I can do is turn it off by holding down the power button.

I can only assume it's the NTFS process that's causing this. I've tried running an instance of [FONT="Courier New"]top[/FONT] in a console, but once it starts the hanging process, I can't bring the window up fast enough. I can, however, unmount the drives within about five minutes of mounting it and not run into any problems.

OS: Xubuntu 8.04
Windows: XP Professional SP2

Thanks for any help in advance!

---

### Post by Jonie on 2008-09-25
It sounds really strange. Could you be more specific about the problem? 
F. ex.: 
Are there any entries in dmesg that relate to that crash?
Are there by chance any bad blocks on that drive?
Did you try "Raising The Skinny Elephant" (if you have no clue what's that just google ;)
What kind of chipset is your mainboard?
Does XP installed on that drive crash too?

---

### Post by kidko on 2008-09-26
I don't have time to check dmesg/etc. because once it happens, my system's gone. I'll try your elephant suggestion next time I feel particularly adventurous (and have a need to mount my Windows drive), but for now I've just got [FONT="Courier New"]noauto[/FONT] set.

XP and Xubuntu are both fine on their own. Until the two mix, neither crashes, hangs, or experiences any difficulties.

---

