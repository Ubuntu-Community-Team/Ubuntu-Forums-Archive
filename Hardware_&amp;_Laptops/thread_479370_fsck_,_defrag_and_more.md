---
title: "fsck , defrag and more"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by rabideau on 2007-06-20
Perhaps someone can help me out.  I have found a couple of posts talking around my issues but not directly to them.

Because fsck runs after 25 reboots and I can only be victimized by its running (I know showfsck tells when I'm going to get hammered again on a restart) what I'd like to do is run something in background that will perform the cleanup function and reset the fsck counter to zero.  I tried defrag but am not certain if that does what I want (in large part because when I ran the tool it asked what type of file system I had, I don't know, and so I aborted the run).

So here are my questions:
[LIST=1]
[*]Is there  an fsck tool I can run in background that will reset my counter to zero while cleaning up any problems?
[*]Does defrag do anything useful?? Should I run it, after I figure out my file structure?[/LIST]Any pointers are appreciated. Thanks!

---

### Post by LaRoza on 2007-06-20
2. You do not need to defrag Linux file systems.

---

### Post by rabideau on 2007-06-20
Thanks LaRoza.

That helps me with one of my dumb questions!  I appreciate it.  I like not having that issue.

Now for the fsck thingee??? This one is a bit of sticky wicket because of the time it takes on a reboot.

---

### Post by LaRoza on 2007-06-20
I don't know about the fsck, sorry.

The questions are not dumb, I wondered about defragging also at first. I did it almost every day in Windows, not realizing it was a Windows issue.

---

### Post by linuxbz on 2007-06-20
Unfortunately, fsck cannot run in the background because the file systems you check need to be unmounted (or  mounted read-only) during the file system check.

However, there is a nice solution. [fsckdown](https://wiki.ubuntu.com/fsckdown) is a script that you can run when you are ready to shut your computer down. It confirms that's what you want to do, then restarts your computer, does the fsck, and then shuts down again.  I run it once a week ... which is fine for the way I do it.

It is especially good if you use a laptop to present something ... it's a pain to have an important presentation, boot up and have to say, "Oh, sorry, it'll be a few minutes while my laptop fscks."
;)

---

### Post by teryan2006 on 2007-06-20
There isn't any tool I know of, but you can use the tune2fs command in terminal to change the number of reboots/mounts before fsck run. The command is: sudo tune2fs -c[number of reboots/mounts] [partition].

Hope this helps.

---

