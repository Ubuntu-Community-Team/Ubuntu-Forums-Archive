---
title: "New to Ubuntu - need help"
date: 2011-03-31
forum: Hardware
---

### Post by Bownz on 2011-03-31
Okay, Well im new to Ubuntu 10.10 and i installed it, all went well. Now when i boot my computer, it boots to a multibooter, and it gives me the option of Ubuntu, Ubuntu (recovery), then two memory test things. And two different windows 7's, and a windows vista.... I boot the first ubuntu and it goes to a black screen and tells me to sign in and i put "ben" in the username and then it wont lemme type any pass and  it only lets me press enter, and then it says wrong login.  :| somehow im on now, i forgot how, but it was something to do with graphics .... IDK, either that or i upgraded some 'G' thing i forget what it was called.

---

### Post by Bownz on 2011-03-31
Okay , after installing 200 something updates, I then restarted. it added 2 more ubuntu options. i picked the first one... It worked fine. Now my issue is, how would i hide/delete the other options, besides for windows 7...?

---

### Post by Dutch70 on 2011-03-31
The 2 new options you're getting are from a kernel update. You really don't want to get rid of the recovery mode options. 

To get rid of the old kernel. Write down the new one so you don't delete the wrong one. Then open synaptic package manager and search for linux-image-2, when they come up, click the box on the one you want to remove, mark it for removal and apply.

You may have to run "sudo update-grub" (without the quotes) from a terminal.

Some people seem to prefer installing Ubuntu Tweak, which will do it for you. It's in software center.

---

