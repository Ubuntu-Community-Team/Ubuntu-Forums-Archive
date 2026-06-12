---
title: "Gksudo Nautilus issues Precise"
date: 2012-06-04
forum: Hardware
---

### Post by ntzrmtthihu777 on 2012-06-04
Hello,

I'm having some issues with nautilus and googled it and saw your post here
[http://ubuntuforums.org/showthread.php?t=1764243](http://ubuntuforums.org/showthread.php?t=1764243)
and was going to try it but there is no .nautilus folder in my home  folder (I unhid the folders with ctrl+h). I can run nautilus fine from  the command line, but when I run gksudo nautilus in order to edit some  root things it will work the first time but will freeze up after a  while, and after i close the window (no other choice) running again  gives no response.

 I would appreciate your help in this matter. I am running Precise on a hp dv9000

---

### Post by ntzrmtthihu777 on 2012-06-04
Hmm... It seems the problem has been fixed; I had earlier modified the /etc/sudoers file to allow a shell script I'm working on to sudo without me entering my password. I deleted the lines I had added and now gksudo nautilus gives no problems...yet. I'm not going to mark this as solved yet, as sometimes a root nautilus ran for a while before freezing on me. If all goes well I shall mark this as solved tomorrow.

Frag, It froze again...URG!

---

### Post by ntzrmtthihu777 on 2012-06-04
Running

[FONT=Courier New]sudo killall nautilus[/FONT]

will allow me to open another root nautilus, but I expect the problem to re-occur.

---

### Post by maureenc on 2012-06-13
Keeps doing the same thing for me.

I am finding glitsches and lock-ups of this kind in lots of places in Precise.

I am beginning to think it may be because I have "opted out" of Unity and have Gnome Session running.... 

Many things don't seem to work smoothly for any length of time and silly but annoying things like setup data mostly being ignored on next startup are getting me a tad frazzled.

---

