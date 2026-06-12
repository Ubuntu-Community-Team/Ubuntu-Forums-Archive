---
title: "Firefox and flash"
date: 2005-11-11
forum: General Help
---

### Post by Skerit on 2005-11-11
About FF crashing when I visit a site which has flash content: I've searched the forums looking for answers but found none... 

Some people say the problem was solved in version 1.5 but I have updated to this version in a long time and am still having thesame problem.

I also read some stuff about the totem plug in not working, already have mplayer plugin but it as far as I know that has nothing to do with flash :)

Removing FF for a reinstall isn't possible on my machine, or I have to uninstall gnome-core, desktop, ubuntu-desktop and all the other important stuff...

I also have installed FF 1.5 (the RC1) over the original folder, but since I had the problem before any of the betas, that can't be it!

I've also tried different versions of the flash plugin without any result!
Here are the logs, but as far as I know there's nothing useful in it...

flashplayer-mozilla: (and nonfree too, ofcourse)
*
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*

libflash-mozplugin
*
WriteReady
Write
WriteReady
Write
*
This is a special one, the page will load but the flash's just black and this 'readwrite' thing keeps on going...
With the mozplugin most of the sites also tell me that I don't have flash ...

---

### Post by dolson on 2005-11-12
I do have Firefox crashing at nearly every flash page that comes up. I've tried the flash plugins in synaptic and the one from installing inside of Firefox too, and no luck. This really bites. I'd like to know what the resolution is too.

---

### Post by simplyw00x on 2005-11-12
> Removing FF for a reinstall isn't possible on my machine, or I have to uninstall gnome-core, desktop, ubuntu-desktop and all the other important stuff...

These are just metapackages. Removing them will not change anything on your system. Also, there's a command in apt-get and an option in Synaptic just to reinstall (it does a remove then an install). This won't cause anything else to be uninstalled.

On the Flash front, the guide in the howtos forum (delete everything Flash-based in the Mozilla directory and then apt-get the correct version) worked for me, but I still have no sound in Firefox.

---

### Post by Skerit on 2005-11-12
I've also deleted every mozilla directory I could find once, don't know if I was thorough enough, I'll try again :)
I even tried to remove my settings ...

At least it's good to know that it won't hurt to remove those packages :)

---

### Post by dolson on 2005-11-12
I'm migrating away from Firefox. So far, Flash Just Works in Epiphany. And it's faster to load normal pages too. I don't know what happened to Firefox, it used to be the fastest, leanest, and best overall. Now it looks like it's falling behind.

---

### Post by jmooney on 2005-11-12
[QUOTE=dolson]I'm migrating away from Firefox. So far, Flash Just Works in Epiphany. And it's faster to load normal pages too. I don't know what happened to Firefox, it used to be the fastest, leanest, and best overall. Now it looks like it's falling behind.[/QUOTE]

I'm getting the same results....having recently upgraded form 5.04 to 5.10, I thought it was a sound configuration problem, then a flash problem.  However, after trying Epiphany, I saw that it was working so it now appears to be a Firefox problem.  

Now, I had a sound problem in 5.04, but the fix was published in the "unofficial ubuntu guide" website.

Anyway, just wanted to echo that the mozilla-engined Epiphany browser does appear to work with flash.

---

### Post by lerrup on 2005-11-13
Well, it doesn't for me.  Flash seems to have died in Konqueror as well.

I blame installing f-spot as it stopped then.  Uninstalling mono doesn't seem to have made it work again either.

Neither does Arnieboy's recent how-to.

---

