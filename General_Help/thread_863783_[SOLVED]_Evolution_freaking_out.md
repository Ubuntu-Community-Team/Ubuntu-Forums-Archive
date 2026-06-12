---
title: "[SOLVED] Evolution freaking out"
date: 2008-07-18
forum: General Help
---

### Post by lsutiger on 2008-07-18
I keep on getting this message from Evolution:
```
Error while Storing folder 'Inbox'.

Summary and folder mismatch, even after a sync
```

It is doubling all the messages in my inbox, even after I delete eveything from my inbox.
Any ideas?

---

### Post by lsutiger on 2008-07-18
Solved by doing this:
Moved everything from my ~/.evolution/mail/local folder to a temp folder. Started Evolution. Quit evolution. Moved the files back

What a buggy program!

---

### Post by whitefort on 2009-04-09
> **lsutiger said:**
> What a buggy program!

You said it!!

A couple of weeks ago, I decided to stop using Thunderbird and give Evolution a fair trial, since it comes as part of the standard Ubuntu setup.

But I really can't believe how bad it is.  It's now stopped working altogether because of the Summary/Folder mismatch error, and after a bit of Googling, I'm shocked that this problem has been around for so many years and isn't fixed.  And doesn't even seem to be given any real priority.

The attitude seems to be - "Here's a workaround.  Do this, Do that, delete this... Jump through this hoop... OK.  See? Now we don't need to fix the bug, because you know the workaround."

No thanks, I want a low-maintenance program that just does the job reliably.

Back to Thunderbird!

---

### Post by dcstar on 2009-04-09
> **whitefort said:**
> 
.......
But I really can't believe how bad it is.  It's now stopped working altogether because of the Summary/Folder mismatch error, and after a bit of Googling, I'm shocked that this problem has been around for so many years and isn't fixed.  And doesn't even seem to be given any real priority.
.......

I have found that having Evolution in the Gnome Session Startup can trigger this problem because other Evolution related things (like mail-notification) also start up and there seems to be a clash of file accesses that is not handled well.

I made a simple script to start Evolution after a 15 second delay and put that into my start up sessions, and my Evolution has been 100% reliable since then.

```
#!/bin/bash
# Evolution starting up on it's own can lock up the Evolution data server process, so delay a little bit:
sleep 15
#
# Then launch the binaries:
evolution-alarm-notify
evolution

exit 0
```

I would guess that the developers just do not use Evolution like most "ordinary" users, and don't encounter this issue in the way others do so they cannot get it sorted out.

---

