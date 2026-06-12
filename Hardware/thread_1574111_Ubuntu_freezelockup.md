---
title: "Ubuntu freeze/lockup?"
date: 2010-09-13
forum: Hardware
---

### Post by jiminportland on 2010-09-13
I just got ubuntu on a dell inspirion 1150 ( 1gig ram 80 gig hd 2.6 meg celeron) and i am having a lot of trouble.  I have a desktop with ubuntu, no probs.  every time i open more than two programs, ubuntu drops my option to close and the locks the bottom task bar.  i am unable to close/restore any of the screens i have been using.  any help?  i am a novice user and as i said no probs i haven't solved on my desktop, but this is annoying!

---

### Post by mikewhatever on 2010-09-13
> **jiminportland said:**
> I just got ubuntu on a dell inspirion 1150 ( 1gig ram 80 gig hd 2.6 meg celeron) and i am having a lot of trouble.  I have a desktop with ubuntu, no probs.  every time i open more than two programs, **ubuntu drops my option to close and the locks the bottom task bar**.  i am unable to close/restore any of the screens i have been using.  any help?  i am a novice user and as i said no probs i haven't solved on my desktop, but this is annoying!

I hope you know what the highlighted text means. Could you explain. While at it, also post the output of the following:

lspci | grep VGA

The output will show the graphics card model.

---

### Post by jiminportland on 2010-09-14
mikewhatever - so far as i understand you are asking for the display info, what i have is a VGA compatible contoller 82852/855GM intergrated graphics controller, not sure that is what you were asking.  as for the other when i have more than 2-3 windows open the  minimize maximize close buttons disappear from the window and the bottom display bar that i can also minimize or maximize from locks and i am stuck with an open window.  sometimes it allows me to close with the file or alt commands, but it never leaves the bottom bar and eventually freezes the whole system.  i appreciate the help.

---

### Post by jiminportland on 2010-09-15
after a reboot i looked and my graphics controller it is listed as Intel 852GM/GME/GMV with a 15" VGA display, hope this helps, if not let me know.  another note; i am having a freeze of the whole system whenever i try to use VLC, could this be graphics card related?  I have ubuntu 10.04 loaded and running no probs on my desktop, but the laptop seems to be most troublesome.  I am watching a movie on the desktop ( .avi ) but the same movie with the same VLC locks my laptop up.  I installed all the repositories that were suggested in the forum ( which is why is works on my desktop) am wondering why it wont work on the laptop?  any help is welcome.

---

### Post by mikewhatever on 2010-09-15
Intel's 8xx chips don't work well with Ubuntu.
For more info and possible workarounds, see the link below.
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

