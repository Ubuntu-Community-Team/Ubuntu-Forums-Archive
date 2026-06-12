---
title: "[SOLVED] vim delete up until a word"
date: 2008-07-30
forum: General Help
---

### Post by PGScooter on 2008-07-30
Hi,

I would like to delete everything from the current point up until the next occurrence of a certain word. How can I do that?

thanks

---

### Post by ashgromnies on 2008-07-30
Put your cursor at the point you want to start at.

Make sure you're in command mode.

hit v to start a visual selection
then hit / and type the word you're looking for to select up to it, then press enter to make the selection
then hit d to delete the text

---

### Post by sdennie on 2008-07-30
You can also just hit "d" then "/" and type the expression you want to match up to.  The same works with "c".

---

### Post by PGScooter on 2008-07-30
great, thanks for the solutions! I think I read Vor's solution somewhere but forgot it. I think this is quite useful.

---

