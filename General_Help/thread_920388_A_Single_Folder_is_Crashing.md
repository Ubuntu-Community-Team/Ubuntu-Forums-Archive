---
title: "A Single Folder is Crashing"
date: 2008-09-15
forum: General Help
---

### Post by cmmichael on 2008-09-15
A few days ago one folder started crashing - that is: when I try to open it, it appears normal for a second or two, but nothing opens. Then it goes gray, and I have to force a close. The folder closes, then the home folder appears in the same spot. 

The only reason I can think of is that it started happening after I saved a few larger jpegs in a folder inside, maybe 12 in all, around 1.5 to 2.0 MB.

---

### Post by eggdeng on 2008-09-15
Maybe an illegal character (something like /, $, ?, \, *,)in the folder name or in a file name? Use the the cd (change directory) and ls (list files) commands from a terminal to check.

---

### Post by Promixa on 2008-09-15
I had the same issue with a folder containing a bunch of svg-files; It turned out that one file was corrupt (don't know why) and i could not open it in inkscape. After deleting that file everything was fine again.

So my guess is one of your jpegs is corrupt;

---

