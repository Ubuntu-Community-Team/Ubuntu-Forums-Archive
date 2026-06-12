---
title: "Aspire One and 3D graphic major problem!"
date: 2008-10-18
forum: Hardware
---

### Post by propofolboy on 2008-10-18
I'm new to Ubuntu so bear with me.

I have a brand new Acer Aspire One A150, I set up dual boot windows xp and clean install of Ubuntu 8.10 beta.
My bios is up to date (3305).  I have all Ubuntu updates.
Everything is working EXCEPT, any 3D graphic windows, when I move them they leave trails and artifact behind.  Eg, gfxgears, and the screen savers..
I have done a complete clean reinstall of Ubuntu, and it still does it.  

I've tried everything to get it to work..
I have no problems with Windows XP and 3D graphics so it doesn't appear to be hardware. 
HELP!

---

### Post by cicatrix1 on 2008-10-18
Googled, and found [this guide to hardy on Aspire One]("https://help.ubuntu.com/community/AspireOne").  I'm sure it's mostly the same for 8.10, but you might be asking for trouble, I'm not sure.  I'm glad to have found this because I plan to get me one of these sometime soon :)

--Matt

---

### Post by propofolboy on 2008-10-18
Ya I've used that guide.
None of the tweaks make a difference.
There is something wrong with either the intel drivers or the opengl or something.  I'm not smart enough to know.

---

### Post by propofolboy on 2008-10-18
Ok, figured out what the problem was...
It was compiz!
I uninstalled mesa-utils and the problem was solved (no artifacts with moving windows with 3d graphics).
I thought it was mesa-utils but that uninstalls compiz with it.  I tried to recreate the problem by reinstalling mesa-utils, but couldn't. 
I then reinstalled compiz, and the problem returned.
Removing compiz (this time alone), fixed the problem again.  
Now I can't use desktop effects though!

Anyone??

---

### Post by propofolboy on 2008-10-18
Further testing reveals that I can have compiz loaded, but have to have visual effects (system - preferences - appearance - visual effects) set to NONE.  It can't be normal or extra.

Argh, I liked my visual effects to!

Anyone have any solution or just have to wait until compiz fixes this?

---

