---
title: "Upgrading 8.04 to 9.04"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by The Real Dave on 2009-05-29
So, having tested out 9.04 on another machine, and through the live disc, I've decided to upgrade from my current install of 8.04.

My problem however is that, after almost half a year of using Ubuntu 8.04, I've got it just the way I want it, my programs just right, appearance, Compiz, start up etc. Things are just how they should be.

But, 8.04, I've found, has its flaws, namely, inability to integrate to my Windows network, lack of support for my Sony Walkman, and problems with hibernation.

So, I want to upgrade from 8.04, to 9.04, somehow keeping or backing up and restoring my settings and programs. 

Also, as a final note, if possible, I'd like to use the 9.04 disc to upgrade my PC, as opposed to doing the upgrade over the net as I've seen in some other forums. :-k I realise that it just makes things more complicated, but my ISP gives me a strict and tiny download limit :( 

Thanks in advance, advice is greatly appreciated :D

---

### Post by lindsay7 on 2009-05-29
. sorry wrong version. I thought you want to go to 9.04 from 8.10.

---

### Post by The Real Dave on 2009-05-29
Nope, 8.04 Hardy to 9.04 Jaunty. :-k

---

### Post by logos34 on 2009-05-29
can't do it.  You can only go up 1 release at a time, or LTS -> LTS (either way, to upgrade from disc you need to use the alternate install cd--live cd won't work)

Despite your issues, upgrading might give you even more problems.  

Maybe you could compile support for walkman.  maybe there's a workaround for hibernation

---

### Post by The Real Dave on 2009-05-29
To be honest, I dont think Im anywhere near good enough at Linux to start compiling code  :-k

---

### Post by logos34 on 2009-05-29
you could do a fresh install of jaunty while saving your desktop settings, not sure about compiz-fusion though...You would shift /home to a separate partition first (link in my sig below, or [this one]("http://www.psychocats.net/ubuntu/separatehome")).

What you could do is this: create the separate /home.  Then, using partimage on the ubuntu live cd, take a snapshot of /.  Install 9.04 over the hardy root (point it to, but do not format, your home on the other partition).  If things don't work out, just revert back to 8.04 by restoring the image.

---

### Post by The Real Dave on 2009-05-30
Thanks for the help mate, I'm gonna give what you said a try. :D

---

