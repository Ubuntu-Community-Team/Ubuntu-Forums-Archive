---
title: "Bitswash .torrent file association"
date: 2008-10-09
forum: General Help
---

### Post by kenji4life on 2008-10-09
After trying transmission and deluge, I ended up with Bitswash, which is an effective torrent downloading program for my specific needs.  I don't know why, but transmission and deluge both worked very slowly, and bitswash doesn't seem to have that problem. 

Anyhow, one thing that I've noticed is that bitswash didn't associate itself with .torrent files, so I have to add them manually.  I have tried making bitswash the default program for running .torrent files by right clicking, clicking properties, and selecting the program, but that doesn't work.  Nor does the 'open with' route.  

I think the problem may simply be that I cannot find the right file to choose.  I tried making a shortcut on the desktop and using that as well, but it didn't work either.

I uninstalled deluge/transmission, as whenever I downloaded a torrent it kept automatically opening with deluge.

I'm running ubuntu 8.04.  

Again, I haven't had trouble changing file associations before with any other program, it seems to just be bitswash that is doing this.  Thanks in advance.

-K

---

### Post by jonian_g on 2008-10-09
Why don't you make the browser open the torrent files with bitswash instead of downloading them and then opening?

---

### Post by kenji4life on 2008-10-09
Sorry if my post was vague or over-worded..  That's exactly what I am saying. 

I have been trying to get it to open directly from the browser.  That is what isn't working.

The only way so far I have been able to open torrent files with bitswash is by navigating to them in the add new torrent option in bitswash. 

What I am asking is if anyone knows what directory to point the browsers open with option to (to use bitswash).  Bitswash doesn't show up on the default list of programs, and I tried /usr/bin/bitswash and home/bitswash/ but that doesn't give an executable to use.  

I don't know which directory the actual executable is in either.  I even tried looking at the properties of the shortcut to bitswash in the applications menu, but that didn't work either.  I'm at a loss.

---

### Post by kenji4life on 2008-10-09
In other words, when I try to point anything to bitswash it just does nothing.

---

### Post by jonian_g on 2008-10-09
Go to system>preferences>Main menu and look at bitswash shortcut to see where the executable is.

---

### Post by kenji4life on 2008-10-09
Again, already tried this.  It points to the /home/ directory and the command is "bitswash".  Putting this in doesn't work.  The best I get is when I use /usr/bin/bitswash, which it allows me to use, but when i download a  torrent file or open a torrent file directly, or even use open with and point to that, it just does nothing at all.

I have already tried the obvious things, including searching for "bitswash" and tried using those executables to no avail.  Does anyone actually have bitswash?

---

### Post by kinu on 2008-11-26
Hi all,

I'm stucked with the same trouble. Any solution?

---

### Post by jaygo on 2009-01-26
you may need to pass arguments to bitswash to have it open a file. In windows, for example, it was often "bitswash %1" to get a program to open a file rather. Check with bitswash devs and see if you can find anything.

also, you might just be having issues with the association. It appears much of the file association settings are in xml files in /usr/share/mime/
Check out this fix for freemind and perhaps you can adapt it for bitswash.

---

### Post by kinu on 2009-01-27
Thank you. I will try.

Best regards,

kInU

---

