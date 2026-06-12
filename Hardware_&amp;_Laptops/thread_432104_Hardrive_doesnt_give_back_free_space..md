---
title: "Hardrive doesnt give back free space."
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by Endoglow84 on 2007-05-03
Hi im kinda new to ubuntu so bare with me if this sounds silly. Okay i have a storage Hardrive just for video and music. When i delete a file i look at the freespace available and it doesnt change no matter how much i delete it just stays the same. Why cant i get my free space back? Thanks in advance

---

### Post by tgm4883 on 2007-05-03
Have you tried emptying your trash bin?

---

### Post by Endoglow84 on 2007-05-03
Yes. This is happening on a second hardrive. When i delete the files they dont go to the trash bin either it just disappears.

---

### Post by taurus on 2007-05-03
What's the output of this command from a terminal then?

Applications -> Accessories -> Terminal
```
ls -la ~/.Trash
```

---

### Post by krazed nun on 2007-05-03
Sometimes, there is a "Trash.(username)" folder created, where deleted files are moved to. This happened on my other comp. I had to empty out that folder too, which was a little annoying. Anyways, after a fresh ubuntu install, it went away. (sorry if i did not help...:( )

---

### Post by louistan3 on 2007-05-03
the trash bin is hidden.. you could jst try and show the hidden files and delete the .trash directory... i mean on the HD that youre talkin about.. :)

---

### Post by scanez on 2007-05-03
They probably go to a trash folder on the second drive itself. See if there is a hidden folder named

.Trash_username

on the second drive and delete that. If you don't know how to see hidden files, hit <ctrl>h in nautilus.

Edit: Wow, beaten to the punch in the 10 seconds I was typing this!

---

### Post by Endoglow84 on 2007-05-04
Thanks you guys are amazing

---

