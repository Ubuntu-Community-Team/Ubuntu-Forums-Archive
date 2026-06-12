---
title: "[SOLVED] are there any rename programs for linux??"
date: 2008-08-13
forum: General Help
---

### Post by itix on 2008-08-13
Hi...

This might sound odd but I need a program to sort files, specifically picture files.

I have about 25 folders with approximately 18-20 subfolders each containing the manga Naruto. I googled, and to my luck, I discovered that thunar has this bulk rename which did me no good. It only alowed me to do minor editing and not the kind of sorting I wanted. 

Ideally, I'd like something like Ex Falso (music tag editor and music manager) that'll allow me to save certain parts of the old file name as variables (like Ex Falso's tags) and then apply those same variables on the new file name. It (Ex Falso) also allow me to create entire directory trees with for example <artist>/(<date>) <album>/<tracknumber> - <title>. The program worked wonders with my music collection, but I wish there were a more general program that allowed me to save parts of file names in simliar varibles.

If none exist, I'd love to get some help starting a new project (and get the damn c-extension for eclipse to work) since I see this as a fairly easily constructed missing feature. I do a fair bit of C coding, and I have a bit of python experience (although only what I learned at the university).

---

### Post by mikewhatever on 2008-08-13
There is a nice music library manager called easytag, though I don't know how it compares to the program you mentioned.
Another simply rename tool is purrr. Both are in the repositories.

---

### Post by decoherence on 2008-08-13
I haven't tried these, but in the repositories you can find gprename and mrename, prefixsuffix, pyrenamer... maybe one of them will do what you need?

---

### Post by itix on 2008-08-13
> **decoherence said:**
> I haven't tried these, but in the repositories you can find gprename and mrename, prefixsuffix, pyrenamer... maybe one of them will do what you need?

Thanks... Searched through the reps but found nothing. I suppose youre better at searching than I am :p

---

### Post by itix on 2008-08-13
Unless someone is sure that prefixsuffix does exactly what I want, I'll just pass it by since It needed about 11 additional packages and that would be mean towards my poor disk space on this Eee (the pitcures are on an external hard drive)...

---

### Post by Vivaldi Gloria on 2008-08-13
KRename (in Repos)
PyRenamer (in Repos)
Bulk Rename Utility with Wine

I use all and like all. The first two have a bit of learning curve cause you have to know the syntax. But easy once you get hold of it. The third one (BRU) is the best but doesn't have a native version.

---

### Post by ilrudie on 2008-08-13
It can be done without installing anything.  The simplest way would probaly be to write a shell script that uses sed or awk to cut up the original filename and output the new file name you want.  Then just cp (safer) or mv (slightly less safe) the old file to the new filename.  For maximum safety cp them to a completly different directory, verify everything is as you want it and then remove the old directory.

---

### Post by itix on 2008-08-13
Thanx, but it would be less time-wasteful to install something. Sure if you chose the scriptway, you look ultra cool on the hidden nerd-camera that broadcast your life to youtube, but I'm lazy.

The PyRename program did EXACTLY what I wanted (patterns), so I'm happy. Thank you for your replies.

---

### Post by decoherence on 2008-08-13
> **itix said:**
> Sure if you chose the scriptway, you look ultra cool on the hidden nerd-camera that broadcast your life to youtube, but I'm lazy.


rotf :lolflag:

here here! (and this from a long time, hopeless bash-addict... i know it's not healthy but at least i'm not on the crack!)

remember to mark the thread [SOLVED] for others who are looking for this solution! :)

cheers,

---

### Post by loboc on 2008-08-13
the thunar filemanager used in XFCE has bulk rename utility thats graphically driven you can install thunar and the bulk renamer without installing XFCE

---

### Post by itix on 2008-08-13
Oh!
Theyve brought back the "solved" system??

I've been away from the forums for way too long.

---

### Post by ilrudie on 2008-08-13
> **itix said:**
> Sure if you chose the scriptway, you look ultra cool on the hidden nerd-camera that broadcast your life to youtube, but I'm lazy.


Dude you were talking about starting a c project to do this!  Just thought you might have been interested in knowing that all the functionality to do this is already there before you started a project.

> **itix said:**
> 
If none exist, I'd love to get some help starting a new project (and get the damn c-extension for eclipse to work) since I see this as a fairly easily constructed missing feature. I do a fair bit of C coding, and I have a bit of python experience (although only what I learned at the university).


Glad you found a solution that meets your space requirements and doesn't require any complicated nerd-cam setups:)

---

### Post by itix on 2008-08-13
Yes??

Your point being?? :P

The mother of all inventions is lazyness. Arkimedes did not invent the Archimedes screw because he wanted to be famous, he was lazy and did not want to carry water in buckets ;)

---

