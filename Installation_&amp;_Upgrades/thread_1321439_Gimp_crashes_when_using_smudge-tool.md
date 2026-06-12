---
title: "Gimp crashes when using smudge-tool"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by lwordish on 2009-11-10
What's up with Gimp in Karmic? On Intrepid it worked flawlessly. Now it freezes pretty much every time I try to smudge an are (the larger are the higher procentage of freezing).

Gimp freezes sometimes when I try do other things in Gimp too, but mostly when using smudge. Some times the entire computer freeze and some times I can get acess to other programs.

Other issues are that I can't press enter to execute with cut tool (looks like a scalpel). I have to click on the area.

Third is that I can't type in Gimp. VERY annoying.

To summit up. How to solve:

1. Freezing when using smudge tool
2. Can't execute cut with enter (scalpel)
3. Cant typ letters or anything in Gimp

I have Gimp 2.7.1 and Ubuntu Karmic Koala 9.10
Acer Extensa 5420G with amd64 processor.

---

### Post by jerrrys on 2009-11-10
GIMP 2.6 was the last stable release, 2.7 is a developmental release. maybe thats why all the trouble.  but i must say that in 2.6 the smudge does not work right for me either...it will smudge a large area at times...

---

### Post by lwordish on 2009-11-10
If it's development release why do they have it as standard in Karmic? (Or have I accidently ticked some box saying yes to development release?)

Installed Karmic on a i386 computer and it looks diffrent than on mine. Guess 2.6 got installed on that one.

Any1 know how I can go back to 2.6?

---

### Post by jerrrys on 2009-11-10
Im running Karmic and 2.6 is the default install.  don't know how you ended us with 2.7.

just delete and reinstall from synaptic or software center and you should end up with 2.6...

also im running 32bit, if your running 64 bit, that could be a different can of worms...

---

### Post by lwordish on 2009-11-10
Uninstalled GIMP 2.7 from Synaptic. Checked Software Recources under System-Administrator. Turned out that I hade "Gimp (Testing) on the source list. Unticked it. When I searched for Gimp again only 2.6.7 was found (yes!).

Hade to completly remove libgimp2.0 & gimp-data before i could install Gimp 2.6.7.

It shows as installed now, but when clicking icon nothing happens. Maybe a reboot will solve that.

---

### Post by jerrrys on 2009-11-10
\\:d/

---

### Post by lwordish on 2009-11-11
A reboot didn't solved that.

Got help from livetech internet tvshow [Category5.tv]("http://category5.tv")

I uninstalled Gimp 2.6 in Synaptic. Used command purge in terminal to be sure Gimp  and all it files where gone. Rebooted, and installed 2.6. And tada, now it works. Got an working 2.6 :).

Thanks Jerry & Category5.tv for the help!

---

