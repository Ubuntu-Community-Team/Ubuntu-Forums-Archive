---
title: "[SOLVED] Removing Vista Bootloader Entries"
date: 2008-08-06
forum: General Help
---

### Post by alexpwalsh on 2008-08-06
Hey all... I've recently been fooling around with various distros and the whole new "Installing while in windows" stuff, but I came accross a problem... with every distro I tried, it created a new entry in the windows boot loader (Vista apparently has one :D). And I couldnt find any fast answer anywhere on the net... so here's how I did it....

After some quick googling I found the name of the new bootloader is BCDEdit.exe, which elegantly stands for Boot Configuration Data Editor... fancy eh???

This led me to find out how to edit these entries.... now do the following only if you are 100% sure that you want to change them, and you know that you either a) Know what your doing (in which case why are you reading this)... or b) are sure that there is no trace left of that distro on your computer OTHER than the annoying boot entry....

OK, so here are the steps to do it... its actually quite simple...

1. Open up a command line, if you dont know how to so this.. then you dont deserve a computer (start>run>type cmd)or just type cmd in the new search bar in vista and hit enter
2. run BCDEdit.exe from any directory.. doesnt matter which
3. look for the ID (identifier) of the entry you want to remove and take note of it... yes its that big long entry of letters and numbers
4. Once you have selected the entry and written it down (or can still see it on screen...) Type the following

bcdedit /delete {THE ID OF THE ENTRY TO BE REMOVED}

and hit enter... and it shuold say something like "Entry Removed Successfully" or something like that....

5. Restart... it's not nessicary, but its always nice to check your work...

Hope it helped.... 

PS: Dont do something stupid like trying to remove the entry that you are currently using... I'm not sure as to what it will do.. but I'm sure its not good... haha... :D

---

### Post by allyant on 2008-08-06
Thanks, I need this now, vista thinks there is two vista's installed for some reason.

---

### Post by PGScooter on 2008-08-06
alexpwalsh,

This seems like a good thing to know.

I think this thread would be better placed in the "Tutorials & Tips" section. Someone who needs to do what you're describing could probably find it better that way.

---

### Post by alexpwalsh on 2008-08-10
your right i'll see if I Can Move it over

---

