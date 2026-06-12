---
title: "Canon Pixma iP6700d malfunctioning"
date: 2013-09-29
forum: Hardware
---

### Post by 3WrKB4C on 2013-09-29
This is a fantastic printer, which unfortunately was not very well supported by Canon with drivers for linux.
It was working with previous versions of cups, then it fell off the radar.
In order to have it working I tried installing the drivers available at ppa:michael-gruz/canon-trunk
I installed the 6600 series, as I understood they are compatible. However, when I try to print, it prints one job only. The second job gets interrupted and the printer stuck (I cannot even switch it off from its key).
Any idea on how to fix this?
Thanks
Luca

---

### Post by aikishugyo on 2013-09-30
Can you try the gutenprint drivers from CVS? Not the outdated test release 5.2.8-pre1 that comes with Ubuntu.
We have a new version of gutenprint (5.2.10) in the works, and I would appreciate any feedback on this printer.
Regards,
Gernot Hassenpflug

---

### Post by 3WrKB4C on 2013-09-30
Thanks for replying.
First of all, in my Lubuntu the version of gutenprint installed is the 5.2.9. I tried to install the new version from the tarball, but during the installation it mentioned that the version I was compiling was the 5.2.9. Logically it showed no different behaviour compared to the one in the repository (I forgot to mention that the first job printed is missing some color, though I can't understand which - however cartridges and heads are fine, as proven by the test page printed from the panel). 
Therefore I guess that the 5.2.10 is only available in the CVS. I could not find detailed instructions on how to get and install that version: can you point me in the right direction?
Thanks

---

### Post by 3WrKB4C on 2013-10-12
I followed your instructions and installed the latest gutenprint from cvs (which, by the way, is still the 5.2.9, although I installed the build from 11 October).
I've run some tests. The situation has improved, since now I can  normally use the printer with almost all applications. Test printing is  perfect, and I also can reproduce all colors faithfully (for instance  with writer),
But I started this to get GIMP print good photos. Also with GIMP now I  can print more than once and the printer does not get stuck. However  GIMP does not yet manage to use all colors for the printer and all  photos are missing magenta component (they are very yellowish).
I suspect the problem is with the gimp-plugin of gutenprint: do you have any suggestion?

---

### Post by 3WrKB4C on 2013-11-09
Bump - Any idea what to do to fix the gimp plugin?
I am now inclined to buy a new printer, but I am also getting tired of all problems I have with ubuntu/linux, maybe it would be cheaper to buy windows...
:-(

---

### Post by Windowsxpnomore on 2013-11-10
Hi, [**[COLOR=#000000]3WrKB4C[/COLOR]**]("http://ubuntuforums.org/member.php?u=1865436")

I have this thead running  [http://ubuntuforums.org/showthread.php?t=2186876](http://ubuntuforums.org/showthread.php?t=2186876), about printing on Canon printers and also have gutenprint release 5.2.8-pre1 installed and it does not print. however support on 13.04 out of the box works without an issues. If someone is willing to talk me thru I'm willing to try updating to the later release of gutenprint. However as I said in my thread I have installed cups 1.6.2 and now screwed things up completely. maybe[**[COLOR=#000000]aikishugyo[/COLOR]**]("http://ubuntuforums.org/member.php?u=167122") could help ?

---

### Post by Nick Payne on 2013-11-11
I've been using Turboprint for a couple of years for photo printing to my Epson 1290, as its capabilities are considerably better than the native 1290 driver, and according to their web site, it also supports your printer: [http://zedonet.com/en_p_turboprint_driver.phtml?&mfg=Canon]("http://zedonet.com/en_p_turboprint_driver.phtml?&mfg=Canon"). You have to pay for it, though.

---

