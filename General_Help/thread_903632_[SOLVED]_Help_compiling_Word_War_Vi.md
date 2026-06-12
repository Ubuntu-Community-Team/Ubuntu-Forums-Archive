---
title: "[SOLVED] Help compiling Word War Vi"
date: 2008-08-28
forum: General Help
---

### Post by GregMB on 2008-08-28
I'm trying to install the game "Word War Vi".

I'm using the guide at [http://www.savvyadmin.com/word-war-vi-in-ubuntu/](http://www.savvyadmin.com/word-war-vi-in-ubuntu/). I've installed every program (except for the gnome-core-devel package, as I'm using KDE) listed, and probably a billion more, but when I try to compile using the "make" and the "make install" commands, it gives me a million error messages and won't do anything. I don't understand the messages, as I'm not a programmer. I really don't know if all this trouble is worth it for one game, but if there is an easy fix, please let me know.

---

### Post by rumplefreakinstiltskin on 2008-08-29
Hello.

I am the author of Word War vi.

What error messages are you getting?

-- steve

---

### Post by rumplefreakinstiltskin on 2008-08-29
Just noticed this:
> (except for the gnome-core-devel package, as I'm using KDE)
This is a problem, as Word War vi is a gnome program (by which I mean it uses lots of GTK and gdk libs and header files.)  The instructions at savvyadmin.com say:
> 
Install Prerequisites and Dependencies

    $ sudo apt-get install build-essential gnome-core-devel portaudio19-dev libvorbis-dev

gnome-core-devel is in that list because it is *required*.

Having the gnome libs and header files around isn't going to harm your KDE setup, (apart from taking up space on your disk.)

---

### Post by GregMB on 2008-08-29
> **rumplefreakinstiltskin said:**
> Just noticed this:

This is a problem, as Word War vi is a gnome program (by which I mean it uses lots of GTK and gdk libs and header files.)  The instructions at savvyadmin.com say:

gnome-core-devel is in that list because it is *required*.

Having the gnome libs and header files around isn't going to harm your KDE setup, (apart from taking up space on your disk.)
 
Okay, thank you. That explains why I'm getting these messages. I'll install those files now. Anyways, even though I haven't actually /played/ the game yet, the concept of the game is really cool.

--------

And it worked!

---

