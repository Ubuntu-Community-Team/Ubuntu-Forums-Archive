---
title: "Help!"
date: 2005-11-12
forum: General Help
---

### Post by theOrange on 2005-11-12
Nautilus starts up fine. I click on File Browser and it starts up in my home directory and i can browse sub directories in my home dir fine.

However, when i click on "File System" or "Computer" and it tries to load "/" it hangs with the CPU at 100%!!! I have to manually kill it!

What could be causing this? I have been running Breezy via fresh install for two weeks now and never had any problems. 

HELP!

---

### Post by theOrange on 2005-11-22
still having this problem where it won't load "computer" - any ideas? The CPU just goes max and nuatilus hangs.

---

### Post by ed_d on 2005-11-22
Post your set up here. Just seems like you are running out of resources....

---

### Post by theOrange on 2005-11-22
[QUOTE=ed_d]Post your set up here. Just seems like you are running out of resources....[/QUOTE]

Thanks for responding...

No - i'm not running out of resources as nothing else is running. 

What setting do you want to know?

Is there a specific log i can look for errors? 

Does Nautilus have a log?

---

### Post by ed_d on 2005-11-22
Proc, mem mainly

---

### Post by theOrange on 2005-11-22
UPDATE:

This is weird - it as like that for about 2 hrs and now it stopped.

Happened last week two. 

Is there a specific config that is causing this or is there a bug in Nautilus i don't know about.

---

### Post by theOrange on 2005-11-22
[QUOTE=ed_d]Proc, mem mainly[/QUOTE]

Where are the logs?

I'll be happy to look at them - just not sure what logs to look at.

(P4 1.7 M, 1GB mem)

---

### Post by ed_d on 2005-11-22
Did you update anything? also did you update to the kernel that is best for your machine?

That may have something to do with it. Im kinda spoiled as I run a 2x 1gb proc with a gig of memory here at work and also have a 2x 1gb proc and 3gb mem at home, so resources arent used up.

So are you using the P7 kernel?

---

### Post by theOrange on 2005-11-22
[QUOTE=ed_d]Did you update anything? also did you update to the kernel that is best for your machine?

That may have something to do with it. Im kinda spoiled as I run a 2x 1gb proc with a gig of memory here at work and also have a 2x 1gb proc and 3gb mem at home, so resources arent used up.

So are you using the P7 kernel?[/QUOTE]

I run the 686 kernel.

This only happened when i tried to browse "Computer" in Nautilus - then it would hang when trying to load '/'.

I really don't think i was out of resources as i would reboot and close everything else and but it would still hang on "Computer".

Why do you think it was my resources?

---

### Post by ed_d on 2005-11-22
if you were running on a machine that had less memory than you had, and possibly a small swap space, I would say that the machine was thrashing thring to free up resouces, such as cpu and memory. Seeing as you have ample resources, I do not know as to why it would hang looking at the filesystems. I have had systems that would appear to hang as they were looking as say the /usr filesystem, but that is because it has a lot of files under it.
Is the system still hanging now when you look through it? Possibly one of the updates that was applied recently may have fixed the "bug".

---

### Post by theOrange on 2005-11-22
It seems to have stopped know. However, when i now open nautilus on the toolbar (the main toolbar) where a pic of the "Comuter" should be all i see is a a doc icon with a red X in the middle.

What is up with that???

---

### Post by ed_d on 2005-11-22
Hmmmmm, that dosent sound good. I was going to see what mine had as the properties, but cant right click on it as it will open. Im sorry, but I do not have an answer for you.

---

### Post by theOrange on 2005-11-22
[QUOTE=ed_d]Hmmmmm, that dosent sound good. I was going to see what mine had as the properties, but cant right click on it as it will open. Im sorry, but I do not have an answer for you.[/QUOTE]

Thanks for caring enought to post. I appreciate it.

---

