---
title: "newbie cant get headphone jack to output sound :("
date: 2008-12-28
forum: Hardware
---

### Post by Bluesymbol on 2008-12-28
hey all...

Ive had a quick scan through the forum and tried a few bits and pieces the best I can... However I am totally new to Linux so it doesn't make much sense to me if I'm honest...

the main problem is that the laptop (fz21z) outputs audio fine through the inbuilt speakers however the headphone jack is another issue. its just blank nothing there...
h
any ideas... already tried reinstalling the alsa driver i think... not 100%. 

any help in stupid person terms would be greatly received :P

cheers
Blue

---

### Post by gettinoriginal on 2008-12-28
Do you also have pulse audio installed ??  If you do, Applications > Sound & Video > Pulse Audio Device Chooser.  This puts an icon on your panel, click it, choose "configure local sound server".  Under Simultaneous Output check add virtual output.  If you don't have pulse, try this How To, it is excellent at solving lots of problems:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

