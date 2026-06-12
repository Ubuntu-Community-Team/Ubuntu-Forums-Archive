---
title: "Ubuntu (Linux) Newbie"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by donzel on 2007-12-08
i've installed Ubuntun 7.10 x86 on my desktop PC. Ive been using DOS and Windows for the past 20 years of my computing life. Im new to Linux. How can I make my Leadtek WinFast TV2000 PCI TV tuner card on Ubuntu? What software to use and view TV? How to install such.


My primary purpose of my ubuntu-based desktop is for internet and TV viewing only,please help.

---

### Post by fain on 2007-12-08
you could install mplayer and try
```
mplayer /dev/video0
```

heres a link to a WAY outdated how to but it might give you some clues to start with. Dont follow it exactly because it is so out dated.

[URL="http://web.missouri.edu/~datcnc/htpc_single.html"]
http://web.missouri.edu/~datcnc/htpc_single.html[/URL]

looks like it uses the bttv driver which is prolly good news

the best application for tv in linux IMO is MythTV. But there are a lot of apps that can access your /dev/video0

---

