---
title: "USB Flash -- Problem with &quot;size&quot;"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by cefola on 2005-09-11
Help !!
How can one tell Ubuntu 5.04 the actual size of
a PNY 1 GB USB flash drive? After deleting a large
file, aproxx 700 MB, then removing the ./trashesxxxx
file, Ubuntu reads the drive as 281 MB not 1 GB?!
Does something need edited ?
Can't find a way to change it.
Any thoughts, suggestions, etc.
Thanks !

---

### Post by Strongbad on 2005-09-11
Have you tryed reformatting it? I use gparted for my drives. It's possible that you have some hidden files on it that are taking up space, in that case, you could type "ls -al" to show all the files on the drive. 

Good Luck!

---

### Post by _cell on 2005-09-12
Check whther there is a hidden "recycle bin" directory on your drive with that 700 Mb file still in it :)))

---

### Post by cefola on 2005-09-16
Thanks for the advice.
I must say that having tried your suggestions and everything else, I'm wondering
if the flash drive itself could be bad?
I only say this 'cause both Linux and Windoze both only see 281 megs and not the
full 1 gig.

---

### Post by _cell on 2005-09-17
[QUOTE=cefola]Thanks for the advice.
I must say that having tried your suggestions and everything else, I'm wondering
if the flash drive itself could be bad?
I only say this 'cause both Linux and Windoze both only see 281 megs and not the
full 1 gig.[/QUOTE]
 Then the only solution I see is to check the drive with some sort of disk tools (like partition magick - sorry, don't know any anaogue for *nix) and fing out whether you'll just need to re-format the drive or it is broken...

---

