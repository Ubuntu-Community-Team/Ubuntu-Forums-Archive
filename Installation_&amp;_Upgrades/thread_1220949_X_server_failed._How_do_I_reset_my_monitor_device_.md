---
title: "X server failed. How do I reset my monitor device? live cd works, but not local"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by rowebil on 2009-07-23
Recently, my laptop screen unplugged. And now I'm getting an X server error.

I put in the live cd, and the screen shows up.

I am not able getinto the local drive from the live cd. I heard you need to change something around.


Basically, i want the screen back. But for now, with a one boot temporary, how do I use console?

If I can fix the screen issue easy, I would like to do that.
If I can't, i just want to be able to boot up, login, and enter the password for keyring and wireless internet.

So, first, If I can get the screen fixed easy, like clicking Install on the live cd, then update, I would like to do that first.

If I can't do that for now, how do I login into console, and put in my password for keyring and wireless internet?

Someone please help me. I posted everywhere on the internet, and no one helps.
:'( Hopefully, I came to the right place.

thank You

---

### Post by sarfarazkazi on 2009-07-23
Boot from the hard disk, press control Alt+Ctrl+F1 to get to the console and issue the command - sudo dpkg-reconfigure xserver-xorg

---

