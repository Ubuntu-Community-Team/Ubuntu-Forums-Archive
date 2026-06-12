---
title: "many  filenames with ~ at the end"
date: 2008-07-11
forum: General Help
---

### Post by clw3388 on 2008-07-11
Anyone else notice ubuntu is leaving many files that already exist and add a ~ so you have duplicates? why?

---

### Post by Elfy on 2008-07-11
Backups usually - very useful :)

---

### Post by jimbob on 2008-07-11
Haven't noticed it myself but I suggest that you are using some sort of program(s) that leave a working copy of the original behind when they exit.  I think vi, among others , does this.

---

### Post by clw3388 on 2008-07-11
> **jimbob said:**
> Haven't noticed it myself but I suggest that you are using some sort of program(s) that leave a working copy of the original behind when they exit.  I think vi, among others , does this.

That may be.. Mostly they are system files for apache and xorg.conf and and and... i use gedit alot.. maybe ill switch to another like vi and see if it stops it.. Its rather annoying to have to run rm -r *~ all the freaking time...

Forestpixie.. Are you suggesting ubuntu is backing itself up??

---

### Post by simonapnic on 2008-07-11
I had that issue myself.
Most of those files were created by Gedit (I use GNOME).
And yes, it's so annoying removing them.

---

### Post by Elfy on 2008-07-11
> Forestpixie.. Are you suggesting ubuntu is backing itself up??

No - as others have said they are usually backups of edited files, which can be useful :)

I use nano mostly now - you have to tell that to make backups I think.

Personally I always have a backup available - bad experience with xorg.conf once.

---

### Post by clw3388 on 2008-07-11
forest.. thought for sure you lost your mind....
haha.. Havn't heard of nano.. i'll look into that..

---

### Post by hal8000 on 2008-07-11
> **clw3388 said:**
> That may be.. Mostly they are system files for apache and xorg.conf and and and... i use gedit alot.. maybe ill switch to another like vi and see if it stops it.. Its rather annoying to have to run rm -r *~ all the freaking time...

Forestpixie.. Are you suggesting ubuntu is backing itself up??


Backups are useful though, Quanta creates files ending in tilde as well.
Here's my cleanup script:


#!/bin/bash
find ~ -name '*~'
sleep 2
find ~ -name '*~' -exec rm {} \;
exit

Just add those four lines to a new file, make it executable, and run it when needed. I call mine .clean  the . hides the filename.
If you create a launcher for gnome, make sure you run it in a terminal.
The first line looks for all files ending ~ in your home directory, sleep 2 pauses for 2 seconds so you can see what its found, then it finds the files again and deletes them. You dont need lines 2 and 3 if you dont want to see whats deleted
You can even add it to crontab if you wanted

---

### Post by tille on 2008-07-11
It's pretty neat, and it takes no space, double all of your text files and it's still nothing in hard drive space.

---

### Post by drs305 on 2008-07-11
> **simonapnic said:**
> I had that issue myself.
Most of those files were created by Gedit (I use GNOME).
And yes, it's so annoying removing them.


Gedit: Edit, Prefeferences, Editor > Untick 'Create backup copy...'

---

