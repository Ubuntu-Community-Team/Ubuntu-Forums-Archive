---
title: "Blank screen after lid closed"
date: 2011-03-03
forum: Hardware
---

### Post by gramirez2012 on 2011-03-03
I have Ubuntu 10.10 installed on a ThinkPad R50e. I changed the power settings so that it would not go to sleep when I closed the lid. However, when I open the lid, all I get is a blank screen and have to turn off the computer for it to come back. I have read that this is possibly an issue with graphics card in this computer. Are there any workarounds?

---

### Post by howefield on 2011-03-03
Have you tried browsing the threads already on the forum, eg

[http://ubuntuforums.org/showthread.php?t=1596545&page=15](http://ubuntuforums.org/showthread.php?t=1596545&page=15)

---

### Post by gramirez2012 on 2011-03-03
> **howefield said:**
> Have you tried browsing the threads already on the forum, eg

[http://ubuntuforums.org/showthread.php?t=1596545&page=15](http://ubuntuforums.org/showthread.php?t=1596545&page=15)

Yep, tried that. :(

---

### Post by iluii on 2011-03-04
I have the same problem with my x41 (for about a year now!), I believe it is a bug with the xorg driver specifically with intel 915 

I tried adding the "do nothing" option to power management with gconf ( as per this posthttp://ohioloco.ubuntuforums.org/showthread.php?t=1443534)  and even though the option to "do nothing" now appears screen still blanks and remains that way. after the latest xorg update the screen now flashes back for one second but goes back to and remains blank

also tried to revert my xorg like this site suggested ([https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4))
but unfortunately the package was not found, Im sure reverting would work since I never had a problem when using 9.04 I believe but Im not really skilled enough to pull that off it seems 

so bump! help please!!

---

### Post by Termo on 2011-05-16
@iluii:

I have the same issue, and for me and others it seems to be kernel related between 2.6.35-19 and 2.6.35-20.

[http://ubuntuforums.org/showthread.php?t=1596427]("http://ubuntuforums.org/showthread.php?t=1596427")

---

