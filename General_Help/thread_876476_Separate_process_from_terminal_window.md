---
title: "Separate process from terminal window"
date: 2008-07-31
forum: General Help
---

### Post by RFGunslinger on 2008-07-31
I use RHEL at school and once I launch a program from the terminal such as "startprogram &", I can then close the terminal window without the program itself closing also.

The default ubuntu configuration doesn't follow this behavior and closing my terminal window shuts down all associated processes launched from that window.  How can I change that?

---

### Post by collinp on 2008-07-31
Well, to do that i think you would need to daemonize the process. Some programs like conky allow for them to be daemonized so you can close the terminal window, but others dont. I am sure there is a program somewhere where you can turn a program into a daemon, but i dont know of one. Mabye a google search will help?

---

### Post by Taxman415a on 2008-07-31
screen is the program you're looking for. And unfortunately that's not the easiest thing to google for tips on how to use. I've used it in the past, but it has so many features the manpage is pretty dense. I did finally find a tutorial that should help:
[http://www.howtoforge.com/linux_screen](http://www.howtoforge.com/linux_screen)
If you don't already have it installed, sudo aptitude install screen will get it for you.

---

