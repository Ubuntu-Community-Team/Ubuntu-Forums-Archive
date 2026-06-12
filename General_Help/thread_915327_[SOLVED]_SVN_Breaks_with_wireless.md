---
title: "[SOLVED] SVN Breaks with wireless"
date: 2008-09-09
forum: General Help
---

### Post by IllegalCharacter on 2008-09-09
Hey everyone,

I have the strangest problem (if it weren't strange I wouldn't be asking, probably would have looked it up by now).

I'm trying to check out repositories via svn to my new laptop running Hardy 64-bit. I'm trying with both my work repository and the JRuby repository over at their site, and both of them seem to just hang for some reason. I obviously have access to the Internet (seeing as how I'm typing this message), and I know the servers hosting the repositories are working fine since I get the whole "do you want to trust this repository, please enter your password" stuff.

I think it has something to do with the wireless, because when I tried plugging the laptop directly to the router, svn checks out the stuff just fine. I've also tried connecting to a different router, to the same effect.

I'm using WPA2 encryption for the wireless, and the wireless adapter is Broadcom BCM4312.

Has anybody seen anything like this, or know what might be causing it?

---

### Post by IllegalCharacter on 2008-09-15
It seems to be a problem with SSH. I'm using ssh+svn for accessing the repository, and I can't seem to SSH into the system when I'm on wireless.

---

