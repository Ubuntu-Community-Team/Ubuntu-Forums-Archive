---
title: "HP PSC 1350 (only scanner no print)"
date: 2004-12-18
forum: Hardware &amp; Laptops
---

### Post by Merlan on 2004-12-18
Hi,

I can use the scanner of my all-in-one printer but impossible to print something. I have hpijs + footmatic + jpoj installed. Everyting seems ok but when I launch a print, the job stays in the queue and waits... ("USB printer is busy").

I installed my printer with the gnome printer manager (local printer). Something strange: I cannot configure the paper and so on in the "properties" menu.

I already read a post on this topic in this forum but I didn't find the solution. I haven't found any ptal-int file (only a perl script).

[http://ubuntuforums.org/showthread.php?t=4360](http://ubuntuforums.org/showthread.php?t=4360)

Please help, the world is so sad without a printer [-o<

---

### Post by mbjbdc on 2004-12-18
did you run ptal-init setup?

---

### Post by Merlan on 2004-12-19
Yep, I ran it when I installed hpoj. I tried again but same result.

---

### Post by Merlan on 2004-12-19
Guys, it works!

Don't understand why, but it works! I uninstalled everything and deleted all hpijs files in a very dirty way. I reinstalled and it worked. It's really a mistery!

I'm wondering whether having Foomatic-bin not installed was the cause of the problem?

Thanks for your reply.

---

### Post by Merlan on 2004-12-19
It works for all applications but Gimp. I know that it's a well known problem but I didn't find any solution on Google.

The Gimp detects my printer as a PSC-1300 and it uses the "Postscript level 2" settings but doesn't print.

Then, I indicated the path to the ppd driver (/etc/cups/ppd/PSC-1300) and I deleted the -oraw option in the command: lp -s -dPSC-1300 -oraw. The job goes to the queue and the printer starts but doesn't write. The result is just a blank page.

I'm lost now! I've CUPS, Foomatic, Ghostscript, Gimp-print, Cupsys, hpijs, hpoj, installed. What do I need more? :confused:


](*,)

---

### Post by Seazzy on 2005-02-21
Hey, I know that this is an old thread, but I have just begun to use ubuntu, and it does not seem to reckognise my hp psc 1350 at all. HOw did you install your printer on to your machine? I am just starting to figure out how to make things work.

---

### Post by nojhan on 2005-03-01
I have installed a hp psc 1350 printer without problem by using the print config system. All you have to do is ti select the good model in the list (hp psc 1300 series).

But I can't figure out how to make the scanner work... Xsane doesn't see it.

---

### Post by grnorton on 2005-03-20
Sigh I have the same problem Can make the Beast print but not scan and here ii seems to be that I need to modify the file that is created by running the ptal-init setup yet all these files are marked as READ ONLY even though I have run sudo -s and logged on as root bu the permissions  Still "see me" as the user and not as 'root'!

The line that I need to activate is

# init.printd.start=0

yet I can t modify the file!

---

### Post by Stefan Koopmanschap on 2005-05-30
grnorton: chmod 755 the file you want to edit, it may just not have write-rights for root either.

I personally have a problem with printing. scanning works fine so it's not a connection problem, but printing just doesn't work :(

---

### Post by ruslan821368 on 2007-05-15
> **Merlan said:**
> Hi,

I can use the scanner of my all-in-one printer but impossible to print something. I have hpijs + footmatic + jpoj installed. Everyting seems ok but when I launch a print, the job stays in the queue and waits... (&quot;USB printer is busy&quot;).

I installed my printer with the gnome printer manager (local printer). Something strange: I cannot configure the paper and so on in the &quot;properties&quot; menu.

I already read a post on this topic in this forum but I didn't find the solution. I haven't found any ptal-int file (only a perl script).

[http://ubuntuforums.org/showthread.php?t=4360](http://ubuntuforums.org/showthread.php?t=4360)

Please help, the world is so sad without a printer [-o&lt;


[magnets demonstrate solar physics Skin care](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

### Post by Buffon2396 on 2007-05-15
> **mbjbdc said:**
> did you run ptal-init setup?


[Debt Consolidation build baking music Bankruptcy](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

