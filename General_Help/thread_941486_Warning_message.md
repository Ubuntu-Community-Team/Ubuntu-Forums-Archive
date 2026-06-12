---
title: "Warning message??"
date: 2008-10-08
forum: General Help
---

### Post by Benbow on 2008-10-08
Just read the following on the net. Is this right, or is it a hoax?

This news has been buzzing around everywhere, but no particular information or result is know as of now.There seems to be a major problem with intrepid(the upcoming ubuntu) and Intel e100e gigabit cards.If you have this card , then it is advisible not to use intrepid as you could screw up your card and cause it to no longer work, yep thats right, using intrepid with this card COULD make your card useless.Although people claim that it has been disabled, its better to stay away from it, especially if you have downloaded an older build of intrepid which doesnt have the patch.
To check if your card is vulnerable to intrepid then type in this command in the terminal and if you get an output that means you shouldnt try intrepid, if you dont , then you could use it lspci | grep 8256[67] .So here's the main thing "There may be a possibility that booting the 2.6.27 kernel found in Intrepid and other recent distributions causes your Intel integrated e1000e network card to be unuseable until it is "fixed" by some not well understood process".
Source : [http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

---

### Post by lisati on 2008-10-08
Intrepid isn't officially released yet, so hopefully someone will have come up with a solution before it becomes official. 

That's the thing about "Beta" software: the developers believe it to be good enough to make available to the public (usually for testing purpose), but there still may be issues to solve.

---

### Post by caleb12 on 2008-10-08
Supposedly this was patched in the last Beta release... The problem was with an EEPROM module in the 2.6.27 kernel, which could "potentially" write back garbage to the EEPROM chip itself overwriting the firmware of the e1000. Not a problem with Ubuntu Intrepid persay, it's a bug in the 2.6.27 kernel. 

It was fixed via a patch at the beginning of the month:

[http://lkml.org/lkml/2008/10/1/368](http://lkml.org/lkml/2008/10/1/368)

Also, the last Beta release of Intrepid has the e1000 module blacklisted in modprobe.d - so seems that they are doing what they can to avoid these problems...

---

