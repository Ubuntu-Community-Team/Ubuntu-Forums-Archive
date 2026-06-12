---
title: "OK I give up - How can I install a dialup modem"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by azumi123 on 2009-10-23
Does anyone know how to get a built in dialup modem to work under Ubuntu?
I have the drivers for the modem - it's Ubuntu itself that isn't seeing it.

Problems: 

1. Ubuntu has no support for dialup (for goodness sake !!!)

2. To get support Gnome-Network-Manager seems to be required 

ok so I use my win98 machine and transfer the sources by flash drive - 

3. Dependencies are required

4. Dependencies need more dependencies

5. Some dependencies have bugs and simply don't compile
(eg. try a google for gettext-tools) 1 week running round in circles wasted. Try finding working binaries - no luck there either. 

6. Repeatedly downloading various sources to attempt a working solution fails or at least I can't find a set of seps that both configures and makes.

Some config but dont make - others just dont make due to bugs.

Also I've discovered make is now case sensitive -
If anyone is having trouble compiling anything at all - try looking for the reported missing files and changing case (probably to upper - this seems widely problematic) I havn't even looked at a C program in 25 years so don't know how universal that is. Just thought the comment may help someone.

Can someone talk me through - ideally with links to where I can get the sources I need (all of them including deps) to get the modem working please? (No - the Ubuntu deps are bugged thats where I started)

I don't have broadband access. 
I can only use dialup on win98 until I get the Linux laptop working
Without it Ubuntu is totally useless to me.

TIA

Az.

---

### Post by davidmohammed on 2009-10-23
presume you've tried the following [howto]("https://help.ubuntu.com/community/DialupModemHowto") link? - you'll still need you win98 to download the relevant drivers though...

---

