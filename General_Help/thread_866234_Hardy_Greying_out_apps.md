---
title: "Hardy Greying out apps"
date: 2008-07-21
forum: General Help
---

### Post by Barnaby Cyneca on 2008-07-21
Hello, I use Hardy Heron Ubuntu and this is getting quite frustrating and I need help. There are some apps that I run (certain games, browser, Applications) that they appear to be running fine but then they get greyed out and either stay greyed out for ever or the turn grey then color returns then they grey out and the program quits. Please help me to know what is happening and how to fix it.

---

### Post by Tim Sharitt on 2008-07-21
A greyed out window is how compiz renders a program which has stopped responding. This could be caused by having too many programs running at once, too many desktop effects enabled, a memory leak in a program taking up too much memory, or a video card driver not working well with compiz (which I think was an issue with my fglrx driver). You con goto System > Administration > System Monitor in the main menu to see how many resources each application is using. You might try to disable desktop effects to see if that helps, although some programs may still lockup but wont be greyed out like they are when effects are enabled. These are just some suggestions, but there may be other causes as well.

---

