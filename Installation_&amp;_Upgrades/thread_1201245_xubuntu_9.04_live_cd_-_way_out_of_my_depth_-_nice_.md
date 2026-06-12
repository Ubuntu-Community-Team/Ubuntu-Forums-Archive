---
title: "xubuntu 9.04 live cd - way out of my depth - nice person to help ??"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by lousuperhands on 2009-06-30
As i said in the title i'm a way out of my depth as i've just jumped into the world that is linux..
I have been studying from the sidelines for a year or 2  tryin out different live cd's just to see whats happening. (slax, Backtrack3 - which was mentioned to me but i honestly dont need that)

Here's my Problem..
Normally when i've tried live distro's they  pretty much load up after an option or 2 and i see a desktop etc however with this one
i seem to stuck on a black screen with text telling me linux software is free blah blah, some security message then ubuntu@ubuntu:

which is where i'm stuck.. is this a loading screen thats crashed, am I to type something?

this was the 2nd disk as the first burn had errors (i used the check the disk option) this 2nd disc was fine... i've tried finding my answer elsewhere but the only clue i have to search is the ubuntu@ubuntu: commandy thingy... (jargon help is a plus)
which in the search gets me nowhere...

Any help? its not an urgent matter.. but if i can get through this i'll be on my way...

p.s my pc is easily in the minimum requirements for this distro.. i already no my soundcard wont work as its not compatible with linux but if i like it i would go with a dual boot..

thanks in advance

---

### Post by ad_267 on 2009-06-30
It sounds like it's booted to a command prompt without loading the X server that gives you a graphical interface. Where did you download the CD from? It definitely sounds like it's a live CD as you're logged in as the "ubuntu" user, but it's weird that it's not loading the desktop.

You could try typing "startx" and hit enter and see if that works.

---

### Post by merlinus on 2009-06-30
Did you checksum your .iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kerry_s on 2009-06-30
we need info on the hardware, since your at command line, start with the type of video card you have.

type> **startx** 
and tell us what the error is.

---

