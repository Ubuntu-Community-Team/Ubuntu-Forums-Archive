---
title: "Pidgin has gone insane"
date: 2008-11-17
forum: General Help
---

### Post by botulismo on 2008-11-17
I'm running Intrepid AMD64, fully updated, and within the last day Pidgin has gone a little wacky. When I attempt to run it as normal, it simply expands my system tray by a few icon widths but doesn't have anything there to click on. The pidgin window never actually appears, and when I run the System Monitor it says Pidgin is running and that it's currently using 50% of the CPU.

It really confuses me because I don't think I actually updated anything and the only "fault" I made between when it was working and when it wasn't was I closed it down manually before I restarted the computer last time... Not a fault, I know, but usually it only shuts down when I shut off the computer.

I included an image to show just what the difference is. It's subtle but it's there. Keep in mind that I am unable to use Pidgin the whole time. I am able to use a version of pidgin (you will see it in the system tray, ignore it, it's the windows version under wine, I would much prefer the Ubuntu version because it runs buggy under Wine.)

The only workarounds that I have used to get Pidgin to work so far are

1.) If I gksudo pidgin, for some reason it works
2.) If I install the windows version with Wine, I can use the windows version, albeit less prettily.

Has anyone had this problem? Does anyone have a possible solution? I've tried installing an older version from the hardy repos but there are unsatisfiable dependencies. :-/

I've also tried running it from the command line, but it doesn't give me any output whatsoever.

Thanks.

---

### Post by Arup on 2008-11-17
The only problem I have with Pidgin is occasionaly it would hog one of my CPU cores at 100%, specially when some animated icons haven been sent from your contacts. This is a listed bug. This looks like some kind of corruption with the GUI layer.

---

