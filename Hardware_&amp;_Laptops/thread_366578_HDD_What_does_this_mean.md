---
title: "HDD: What does this mean?"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by newbie22 on 2007-02-21
My HDD is running fine.  Then I hear a noise.  The HDD shuts down.  Then comes back on.  But everything on screen eventually freezes.  Except for movement of the cursor.

What does this mean?

---

### Post by maher on 2007-02-21
if the cursor moves, is there a chance that the keyboard works too?
if your keyboard is responding type:
ctrl+alt+f2
log into your account
and 
type dmesg
if there is an entry at the bottom which has something to do with hd could you please post it

if your keyboard doesn't respond, and you have another computer running a linux distro try ssh to access tour machine and follow the steps described above.

hope this helps

---

