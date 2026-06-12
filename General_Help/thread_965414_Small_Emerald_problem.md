---
title: "Small Emerald problem"
date: 2008-10-31
forum: General Help
---

### Post by johnrhance on 2008-10-31
I seem to have encountered a small problem using Emerald to manage my themes. When I change the theme, it doesn't automatically change so I have to do "emerald -- replace" in the terminal. That works fine and I don't have a problem with that, but when I close that terminal window, it kills the theme. Is there anything I can do to prevent that? Thanks.

Specs:
Lenovo Ideapad Y430
T5800
3gb
Intel x4500 integrated video
Ubuntu 8.10 Intrepid

---

### Post by cgkades on 2008-10-31
there are a few things you can do. funny, i just fixed this problem for myself. here is what i did. i opened the advanced desktop effects settings, if you dont have it search for it in the package manager. go into window decoration and change the command to from "compiz-decorator" to "emerald --replace" leave the rest of the path though. you'll have to reboot if you dont want to make your system use emeraldt. you can type "nohup emerald --replace" in the terminal every time you want to run it.

---

### Post by johnrhance on 2008-10-31
I can't find the line that says "go into window decoration and change the command to from "compiz-decorator" to "emerald --replace"". I'm looking in CCSM, but it is nowhere to be found.

---

### Post by cgkades on 2008-10-31
here is a screenshot of the window decorations thing and where the line is. if you have 8.10 it's there. it took me a while to find it on my other system that has 8.10. i'm using 8.04 on this system though

---

### Post by johnrhance on 2008-11-01
Found it and changed. We'll see if that works. Thanks for the screenshots.

---

### Post by chemburn on 2009-01-24
Hey John, I was just wondering, I have the same model laptop, just bought it actually tonight. I am noticing a strong lack of success stories getting all the hardware working on ubuntu, well it has vista 64 now, and that won't be staying, I am really bummed if I can't use Linux, and I was wondering if you could let me know how well your system took to the install and if there was an awful lot of tweaking that was involved. Does all your hardware work etc. etc?

Any helps, hints, warnings or info would be greatly appreciated.

J--

---

