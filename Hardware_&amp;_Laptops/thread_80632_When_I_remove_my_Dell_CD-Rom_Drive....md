---
title: "When I remove my Dell CD-Rom Drive..."
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by bubba on 2005-10-22
to swap it with my extra battery, while the machine is up and operational, it locks up.

Any special tricks or things you have to do before you remove such drives?

I think the machine is a Dell C610.

---

### Post by Chuckaluphagus on 2005-10-24
There is a program for this that you can install through Synaptic called "hotswap". (There is the command-line version called "hotswap" and a KDE graphical version called "khotswap", I believe).  It has to be run as root, but it's quite simple.  I just open up a terminal and type "sudo hotswap" at the prompt.      The instructions that follow are very clear, and once it says you can remove the drive you can do so without causing any lockups or errors.

I use this with my own notebook, an Asus M3Np, so I can't say for sure that it'll work with yours.  I'd assume it would, though.  Good luck.

---

### Post by bubba on 2005-10-26
ahh.. it seems to work great!  Thanks for the info.

Brian

---

### Post by Chuckaluphagus on 2005-10-28
Glad I could help.

---

