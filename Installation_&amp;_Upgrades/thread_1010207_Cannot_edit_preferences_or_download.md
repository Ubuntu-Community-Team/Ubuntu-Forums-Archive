---
title: "Cannot edit preferences or download"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Madwand on 2008-12-13
I recently upgraded from Hardy to Intrepid, then had to downgrade back to Hardy. I moved my Home folder to a new partition before doing this, so my data was saved. However, I am experiencing something very strange now, and I think it is all the same problem: I cannot edit many preference settings, or download files or install plugins in Firefox. For example, when I access "User switcher preferences", the window is greyed out and says "Some preferences have been locked by the system administrator". I have the same problem with editing panel preferences, or any other preference setting. I'm fine if I use sudo in the terminal of course.

If I try to download a file in Firefox, the download window doesn't pop up and nothing happens. Same thing if I try to install the flash plugin (which is already downloaded through Synaptic). I've experienced many other strange symptoms of not having permissions to do many other activities.

What can I do to correct this problem? I wonder if this might have something to do with Intrepid messing with something on my home folder, or is it something else?

---

### Post by albinootje on 2008-12-13
Perhaps the easiest is to create a new user, and then start to copy prefs.js and bookmarks.html from the .mozilla/ directory from the original user.
Likewise for other data that you need.

---

### Post by Madwand on 2008-12-13
I'd like to understand the root cause of this problem, as much for educating myself as anything else.

I discovered another symptom that seems to be the cause of all the previously discussed problems: I get "permission denied" errors doing anything in the terminal on the old files. If I even try to write a new file into an old directory, I get errors (although I can create files in the base directory and later edit or delete them normally).

I can change ownership of files, and change permissions, but not even doing a "chmod 777" on these files will allow me to delete or edit them. The files also seem to show that I own them. So, what could possibly be causing these "permission denied" errors, and how can I fix it?

---

### Post by albinootje on 2008-12-13
During a fresh install the first user being created during the install will get uid 1000.
It is likely that your new user also has uid 1000.

But the reason i wrote down my suggestion was that i expected your "newer" settings not to play nice with your "downgraded" Ubuntu-release.

I don't see a cause for the permission denied errors :(

If your user is called adrian, did you perform a :
sudo chown -R adrian:adrian /home/adrian/ ?
Perhaps that'll help.

---

### Post by Madwand on 2008-12-13
The "sudo chown" command worked! I tested it out first in a directory I didn't care about... but I noticed that it gave me ownership of everything, even things that were owned by "root". Should I be concerned about this? Is there a command that will only give me ownership of things I _should_ own, and leave root ownership untouched (if this is even necessary?)

---

### Post by albinootje on 2008-12-13
Normally everything in your own home directory should be owned by you.

(Unless you're on a multi-user system where the sysadmin doesn't want you to change certain things.)

---

