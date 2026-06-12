---
title: "graphics trouble with two monitors"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by HugoRune on 2008-02-07
Hi

I just updated my laptop to ubuntu 7.10

Initially the grahics worked fine, but I could not clone the display to my external monitor like I could before. 
Previously I could use the higher resolution of the external monitor (with the drawback that not the whole desktop is visible on the laptop, but that was ok). Now it was limited to the maximum resolution of my laptop, which is very low.

I tried changing settings in the "screen and graphics preferences". I changed resolution and switched the primary monitor.

Now ubuntu always starts in low graphics mode, even when there is no external monitor atached. There are three monitor and two graphic card entries in the "screen and graphics preferences" and I cannot switch it back


So, my first question: 
How can I undo this so that at least my display works again?


second question:
how can I get the external monitor working like in the previous ubuntu version?


Thanks for any help

---

### Post by HugoRune on 2008-02-07
Someone gave me the tip to try 
"sudo dpkg-reconfigure xserver-xorg"
That program apparently solved both problems at once after asking a number of mostly incomprehensible questions.

(If anyone else needs to try this: some dialog boxes can be confirmed with enter, but some only with alt+enter)

As a side effect my xorg.conf got a lot smaller. I hope I broke nothing else by that

From my previous experiences with ubuntu, the word xorg.conf alone can give me nightmares.

so, I still have no idea what I did wrong or how I fixed it, but it works again :)

---

