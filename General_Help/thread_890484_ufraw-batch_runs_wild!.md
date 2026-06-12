---
title: "ufraw-batch runs wild!"
date: 2008-08-15
forum: General Help
---

### Post by perstromgren on 2008-08-15
I have on two occasions had ufraw-batch run wild on my system, spawning a large number of processes, which lead to the desktop freezes, probably because the system runs out of resources.

Some facts:

1. I did not execute ufraw-batch myself.
2. I do have Nikon NEF files on the system.
3. I think that the problem occurred both times when I renamed directories containing pictures.
4. Re-booting does not seem to help, ufraw-bacth starts happily after re-boot. It ran all night, last night, without generating any (visible) result.
5. It has happened both under Ubuntu 7 and 8.
6. I don't remember how I stopped it the last time this happened.

Help, ufraw stole my computer!

Per.

---

### Post by pekka72 on 2008-08-17
Same problem here. I'd really like to know which deamon starts this. I uninstalled ufraw in the meantime.

---

### Post by hoakz on 2008-09-05
I'm sorry to report I have the same problem.  I did not, however rename any folder with NEF files.  I do have them though.  However I did not install ufraw on my system.  Did not have the problem in 7.  Believe the problem might have started after installing digikam but it uses dcraw!  Otherwise I'm clueless :(

---

### Post by hoakz on 2008-09-05
Found this, however it turns out I'd already turned off Tracker:
[http://www.edspace.com/blog/?p=161](http://www.edspace.com/blog/?p=161)

Could be that beagle does the same... it has an ignore files tab as well, perhaps if I add *.NEF...

To do this in beagle open the search dialog, choose Search->Preferences, and then the tab indexing, there you'll find a list of paths and file patterns under the heading Privacy, add "*.NEF" or "*.RAW" or similar, make sure it's added as a filename pattern.

Update: well it turns out even though I have disabled trackerd in my sessions settings I have a trackerd process... just another curve ball this "new and improved" version of ububtu is throwing at me?

The command from the above link helps though.
> killall -9 trackerd

---

### Post by hoakz on 2008-09-06
1 day later and I still have no runaway ufraw-batch process.  Seems the above info helps!

---

