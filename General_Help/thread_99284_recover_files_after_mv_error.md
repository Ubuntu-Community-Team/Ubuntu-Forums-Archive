---
title: "recover files after mv error"
date: 2005-12-05
forum: General Help
---

### Post by earth_walker on 2005-12-05
Well, I had my first dumb move data loss today.

While installing Firefox 1.5 this morning I made a typo and didn't realise I was in the wrong (home) directory before trying to do a 

[INDENT]mv * ~/.mozilla/firefox/*.default [/INDENT]

It gave me an error, didn't move anything into the default directory, but did  erase EVERYTHING in my home directory except my desktop. I've searched the filesystem (using the gnome tool) and checked the trash to no avail. 

Anyone have any hints as to where these files might disappear to? Is the graphical gnome search getting everything, or should I use a command line?

Is there any 'undo' possible?

and finally, Why the hell would mv erase things it hasn't moved????

Edit: It didn't erase everything in my home directory - all the hidden files are still there, but none of the regular directories survived.

---

### Post by xmastree on 2005-12-05
Best I can think of is use the search to find  something you **know** was there.

Edit: tell it to start at the top. i.e. /

---

### Post by mherring on 2005-12-05
It looks like you tried to rename multiple files to one new name.  I just tried that and mv simply gave an error  "when moving multiple files, the target must be a directory"

First---do not write anything to your disk---the bits are still there somewhere and can likely be recovered with data recovery SW.

Try using the file finder---being sure to enable hidden files and folders.

Then, try something like dd and hexdump to look at actual raw data  (or find some data recovery SW)  
WARNING: unlike other commands, dd can really destroy everything with no chance of recovery---use with caution.
I will try to find the electrons for a killer tutorial on dd---otherwise try a Google search.

---

### Post by earth_walker on 2005-12-05
Thanks to both of you. 

Everything was accidentally moved into a hidden folder, and so all I had to do was to enable hidden files and folders in my search session, and they came right up!

For others, if you cannot find some files or folders then try:
Files --> Search for Files

Click "Select more options"
Choose "Show hidden and backup files' next to "Available options" and click 'Add'
Then try the search.

---

### Post by mherring on 2005-12-05
Glad you recovered....

I found the dd tutorial and will post as a new thread.

Is this a good time to mention "backup"?

---

