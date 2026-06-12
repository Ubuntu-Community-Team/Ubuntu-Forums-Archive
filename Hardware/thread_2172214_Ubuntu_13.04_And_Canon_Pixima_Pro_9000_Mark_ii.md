---
title: "Ubuntu 13.04 And Canon Pixima Pro 9000 Mark ii"
date: 2013-09-03
forum: Hardware
---

### Post by travis7 on 2013-09-03
So I plugged in my Canon printer today, a "Pixima Pro 9000 Mark II" and was able to find the driver by manually searching the drivers list in the printer install dialog. But whenever I print, the text seems to cut right off the edge of the paper "as if the printer is expecting the paper to be larger". However, I have it configured for Letter paper "8.5 x 11" and I am using Letter sized paper. o.O 

So I looked through the config, and its set to shrink the content to the page, which it is probably doing, but it seems to not be calibrated at all to the page. :| 

Any ideas?

---

### Post by travis7 on 2013-09-03
Just did another check up. It seems all pages get cut off. If I print on 8.5 x 11 letter paper. But set the settings to 4x6, it prints a 4x6 frame, but it is still cut off. o.O; Not sure what to make of that.

I currently am using gutenprint (latest version)

Marked as Solved.... for now. I seem to have fixed it by re selecting the printer driver again, and setting the ink type to CMYK. How that fixed an alignment issue, I have no clue.

---

### Post by aikishugyo on 2013-09-05
Hi,
I am the Canon gutenprint maintainer. Thank you for the feedback. However, what is the "latest version"? I would think the latest version is 5.2.9, but maybe not in Ubuntu. If you are using 5.2.8pre, then please upgrade to 5.2.9 somehow (from source, or from someone else's repos, check the Ubuntu PPA that people have put out there for this purpose).
5.2.8pre is a pre-release, with many bugs.
If the problem exists in 5.2.9 then I need to ask a few more questions. I can tell you why inktype CMYK solved the issue: setting an inktype changes the possible resolution modes that can be chosen, so you ended up with one that works.
In Canon printers, the resolution mode is dependent on:-

[LIST=a]
[*] the resolution (as a user you don't get to choose this, and it is either 300 DPI or 600 DPI, or in some printers there is one mode also of 1200 DPI);
[*] the media (plain, Photo Paper Gloss 2, etc.);
[*] the inktype (one of various meta-color sets in subset of CMYKcmyk*** <- whatever other inks Canon supports in the driver: these are not the physical colors you put into the printer;
[*] cartridges (in some printers you can select between Black-only, Color-only, or Both)
[*] Duplex (duplex often uses different modes with less ink density so as to not run ink when putting media through the printer again);
[*] Borderless (borderless uses color-only modes for printing, since it is intended for photo printing, and only supported on some media. For plain media, a special color-only fixed quality mode is available).
[*] maybe some other parameters I cannot think of right now (media tray perhaps also for some printers).
[/LIST]
These data are sent to the firmware which then utilizes some algorithm to print on the media desired with some colors and use of the printhead so as to give an image which is then advertised as some particular resolution (max 4800 or 9600 dpi for example) depending on how many passes the printhead makes I suppose.
Needless to say, if the parameters are incompatible with what the firmware understands, the printer will not be able to print. It does not have the intelligence to substitute something workable based on some priority of parameters.

So that is what we try to implement in the gutenprint driver. If a user does not set anything, which seems to be the norm for some strange reason I cannot fathom, then the default media (plain) and resolution (set in the driver per printer, usually the 2nd-highest or highest quality for plain media), default tray and so on are used. This should work, but most printers are experimentally supported, so unless we get feedback, we do not actually know if something is missing in the code (extra commands needed, bug in the code, etc.).
We then programmed a hierarchy of parameters, so that the driver can always find a legitimate combination of parameters given what the user inputs. If you change a parameters with a high priority, the decision cascades down the other parameters so that the resulting list of possible "resolution modes" will be different (e.g., no overlap at all between plain media and photo media).
I hope that gives you an idea of what is going on.
To get more details, you would have to set CUPS debug on, and look at the log file to see what modes are actually chosen in gutenprint for whatever settings you are using.
Cheers,
Gernot Hassenpflug

---

