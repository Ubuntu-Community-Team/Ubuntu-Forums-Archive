---
title: "Gnome lockup?"
date: 2005-01-02
forum: General Help
---

### Post by Beto on 2005-01-02
Hi,
My copies of ubuntu 4.1 arrived so I wanted to give it a try.
I have an old PC, a Pentium II 333Mhz, 192Mb RAM, sound blaster awe 32 and an 8Mb ATI all-in-wonder.

The loading starts but when once the load stops, the graphical enviroment doesn't work.. no mouse.. no keyboard, etc... I pressed CTRL+ALT+F1 and there were some errors and one of them was related to gnome and sound. I was a bit frustrated so I didn't write it down. I saw a little bit above and there were more errors. My sound card wasn't recognized, etc... 

I booted again in verbose mode to see what was happening and there were some errors that I can't understad, giving how new to linux I am. Is there any log where I could read the entire startup messages. I can use the shell in another "terminal" (e.g. Ctrl-alt-F2). If I can do this, how do I mount a partition to save the log file there?

My idea is to post this log here so someone with the knowledge can help me.

Regards,
PS: I tried failsafe mode and the result was similar.

---

### Post by eco2geek on 2005-01-02
A guess is that it's having problems with the video driver. Try typing "xmodule=ati" (without the quotes) or "xmodule=vesa" at the end of the GRUB prompt. Or it may be having problems figuring out your monitor's correct sync rates (see the [Morphix Boot Options](http://www.alextreme.org/phpwiki/index.php/MorphixBootOptions) page for more info about that).

(The GRUB prompt is that long line of text you see at the bottom of your screen when the Ubuntu live CD first boots. There's a cursor at the end of it, and you can just start typing.)

---

