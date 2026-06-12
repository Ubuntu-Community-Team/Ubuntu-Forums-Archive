---
title: "sony dvd rw drive"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by danip on 2005-03-19
I have a sony dvd rw drive that is run via USB2.  How can I get linux to recognize this.  I have it plugged in and nothing pops up like my external hard drives do and when i go places>computer it does not show up there either.  Maybe ubuntu is picking it up and i just do not know how to access it any.  Any help much appreciated.


Also this is off topic but my homepage is set to [www.whatufind.com](www.whatufind.com) and it will not change even when i go edit>preferences on firefox, its like im having a spyware attack on windows again :S

---

### Post by danip on 2005-03-21
bump

---

### Post by alastair on 2005-03-21
Re; DVD USB drive

Boot with out it plugged in.

In a shell :

sudo tail -f /var/log/syslog

This "tails" kernel log messages - you see them as they are written.

Then, plug in the USB drive. Anything printed?

Re: firefox homepage

Not much of an idea. Perhaps start firefox from a shell i.e. type in a terminal :

firefox

Change your home page. Any warnings or errors relevant in the shell?

---

### Post by endless on 2005-03-23
Regarding the first problem: I think I'm having the same problem: a USB cd drive that doesn't get detected. It works fine in Warty, it works fine in Knoppix, but something in Hoary in its current state broke it, and I have no clue. Anyone has an idea, or should I just wait? :confused:

---

### Post by Syrinx on 2005-04-25
[QUOTE=danip]
Also this is off topic but my homepage is set to [www.whatufind.com](www.whatufind.com) and it will not change even when i go edit>preferences on firefox, its like im having a spyware attack on windows again :S[/QUOTE]

In the menu propeties for FireFox, take out the %u.  All you really need in there is "firefox".

The %u is used to open up Firefox to a clicked link.  You'll only get the whatuseek.com if you open the browser for the first time.  Everything else will work fine; even clicking on the HOME icon.  It's not spyware, it's a script issue with the browser.  

I had this problem and was in an e-mail conversation with some of the Firefox programmers for a couple days.  It was them that said to take out the %u.  It worked!

---

