---
title: "Battery Saving Mode &amp; Graphics Mode"
date: 2008-05-08
forum: Hardware
---

### Post by dahc2424 on 2008-05-08
I have gathered a lot of different things to do to increase battery life on a laptop through the forums.  I want to be able to make a batter saving session that I can log into or a "normal" mode that has all the fancy graphics etc that kills battery life.  Is there a way to create 2 "sessions" so when I login to my account I can choose which one I want.  I tried creating to user accounts but when I changed settings in 1 account it affected the other.

What is the best way to do this?

---

### Post by sdennie on 2008-05-09
You could just put all your power savings options in a script and, at the bottom of the script run, "metacity --replace".  That will turn off compiz.  Then, in another script, put the options that reset your machine back to full power and, at the bottom, put "compiz --replace", which will start compiz again.  You can then create launchers for the scripts and you can toggle back and forth between the two at will without logging out.

---

