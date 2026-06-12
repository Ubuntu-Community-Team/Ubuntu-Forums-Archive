---
title: "[SOLVED] user cannot issue umount (bad things happen)"
date: 2008-10-28
forum: General Help
---

### Post by soro2005 on 2008-10-28
Since several weeks ago, I have the following problem: Whenever a user other than su issues any command beginning with umount, the gnome terminal in which the command is issued spawns an unstoppable barrage of processes named bash, leading to full CPU usage and some seriously clogged memory, etc. This seems to be independent of the actual device that I try to unmount. It even happens with umount -h.

If I do the same in a tty without an x server, I get the following error:
```
malloc: ../bash/dispose_cmd.c:241: assertion botched
free: called with unallocated block argument
Aborting...
```
Anyone with any idea what this could be about, or how to troubleshoot it? This is with Hardy 64 bit.

---

### Post by dkaplowitz on 2008-10-29
Oddly I'm getting the error with a script that calls ssh. The script is literally ssh username@somehost.

I'm running the 64-bit desktop version of 8.10.

---

### Post by doobliebop on 2008-10-30
Very strange. I have a python script that works fine when I type:

python scriptname.py

If, however, I set the script to be executable and just ./scriptname.py it, I'm getting the same error message... 8.10 64 bit. Hope this gets resolved...

---

### Post by cariboo on 2008-10-30
If all three of you are having the same problem, at least one of you should create a bug report. You can do it here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

If the developers don't know about a problem they can't fix it.

Jim

---

### Post by soro2005 on 2008-10-31
> **cariboo907 said:**
> If all three of you are having the same problem, at least one of you should create a bug report. You can do it here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

If the developers don't know about a problem they can't fix it.

Jim

That is sure true, but it is not quite clear to me what developers to notify here. Without that, it's difficult to make a decent bug report.

Do you folks get the exact same error with reference to dispose_cmd.c at line 241? Or just something that sounds roughly similar?

---

### Post by the_czar on 2008-11-04
I am having the same exact problem.  If I try to run a shell script with the ./ command, I get the same error.  If I execute the script using the source command, it works perfectly.  I too am running 8.10 64-bit.

---

### Post by soro2005 on 2008-11-05
> **the_czar said:**
> I am having the same exact problem.  If I try to run a shell script with the ./ command, I get the same error.  If I execute the script using the source command, it works perfectly.  I too am running 8.10 64-bit.

What is in your shell script? Also, what exact error do you all get? The exact same one in dispose_cmd.c:241? Or just something with malloc?

We have one umount here, one whose python script produces an error, one whose problem might be in ssh, and one not further specified. Perhaps everybody could just be a little more detailed and specific, so that we can have a more qualified assessments whether all of our issues have to do with each other.

---

### Post by soro2005 on 2008-11-05
Ok, marking this thread as solved. Obviously, there might be a bug in bash, but since people are just raising their hand and saying "I too have a similar problem" but then not following up, we are not going to find that out here.

As for my umount trouble: I had, very stupidly parked some entirely useless text file in a directory called ~/bin and for some entirely stupid reason called it "umount." On invoking the command, poor and innocent bash then didn't know what to do.

So what I learn here: Don't fool around in your ~/bin directory if you have one. Specifically don't populate it with files that might interfer with legitimate commands and utilities. :mad:

:idea: Now, reading through the thread again, I have one idea: My useless trashy "script" didn't have the #!/bin/bash at the beginning, and sure enough, when I put it, the malloc error doesn't seem to occur. Might that be the problem in your scripts as well? :idea:

---

