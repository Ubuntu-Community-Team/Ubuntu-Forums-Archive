---
title: "dmrc and gvfs permissions problem"
date: 2008-10-17
forum: General Help
---

### Post by Jack-_- on 2008-10-17
I'm experiencing a combination of two frequently-reported issues.  

When I start Intrepid I get a message saying:

> "User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

The [solution]("http://ubuntuforums.org/showthread.php?t=371052") ([and here]("http://ubuntuforums.org/showthread.php?p=5598208")) is to change the permissions for .dmrc and my folder to user.

I can change the permissions for dmrc, but when I try to change permissions or ownership for my home directory I get:

> cannot access '/home/(user)/.gvfs': permission denied

That problem has cropped up for people [trying to sync or backup their home directory]("http://ubuntuforums.org/showthread.php?t=791693").  The solution for them is to --exclude gvfs, but I can't do that with chown or chmod.

I also canpt find .gvfs in the home directory.

Any ideas on how I can fix this?

---

### Post by captinkid on 2008-12-23
I have the same .dmrc problem with my 8.10 installation. I installed it from scratch so I don't think it was anything I did.

I tried changing the permissions and even tried deleting and replacing the file. No good.

I don't have the .gvfs problem.

---

### Post by Elfy on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

Have a look here captinkid

---

### Post by captinkid on 2008-12-23
> **forestpixie said:**
> [http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

Have a look here captinkid

Thank you, that solved the .dmrc problem.

---

### Post by drs305 on 2008-12-23
Too late, forestpixie has you covered. 

To solve the .dmrc problem you do not have to use the -R (recursive) switch. Here is a tutorial and solution to $HOME and .dmrc problems. 
[URL="http://ubuntuforums.org/showthread.php?t=976610"]Solving .dmrc and $HOME Permission Errors
[/URL]

---

