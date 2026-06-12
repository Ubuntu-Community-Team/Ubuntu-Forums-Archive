---
title: "Scrambled screen graphics and freeze after login"
date: 2009-04-07
forum: Hardware
---

### Post by daufhammer on 2009-04-07
This is my first time ever using Linux. I am pretty good with computers and really know my way around windows. I got ubuntu 8.10 all installed on an old PIII 1Ghz 512mb computer i had laying around. It worked the first time or two i used it, but then i tried to hook it up to my HDTV to use that as my monitor. After i logged in all i got was some scrambled colors and then it froze. I tried hooking it back up to my normal lcd monitor and now it doesn't work with that at all either.  I think my computer has the Intel 810 chipset for video.

Any help would be greatly appreciated.
Thanks,
-Drew

---

### Post by SynthesizersFTW on 2009-04-07
Hi Drew,

Assuming you see the POST and boot sequence OK before you get to the logon screen:

Boot up the PC, when you get to the GRUB menu (or hit ESC to display it), choose the recovery kernel option.  From there it should take you into a text menu where you can select an option "xfix" - your X.Org configuration went berserk the moment you tried switching to the HDTV monitor, and xfix should repair it.  As far as your HDTV goes, it will probably take some doing to get working, but for now just stick to the LCD, since it's "known good" ;)

For a gentle introduction to the linux GUI:
[http://en.wikipedia.org/wiki/X.org_Server](http://en.wikipedia.org/wiki/X.org_Server)

There exists a way to import the right settings into your /etc/X11/xorg.conf by using the Windows .inf file that comes with Windows monitor drivers, but the actual steps escape me at the moment - I'm thinking it might be found in the Monitor settings panel.  I hope you can find a Windows driver for the HDTV, or else you may have to hack the proper settings (resolution, refresh rates, etc.) from the spec sheet.

Good Luck!

---

### Post by daufhammer on 2009-04-07
Thanks for the help. I tried xfix, but it didn't work... i still get the same scrambled graphics and then it freezes when its trying to load the desktop after i log in.

Any other suggestions or help would be appreciated.

Thanks,
-Drew

---

