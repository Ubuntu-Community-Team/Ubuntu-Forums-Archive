---
title: "[SOLVED] Evolution Folder OK, but Setting...not so much"
date: 2008-11-14
forum: General Help
---

### Post by mlissner on 2008-11-14
I have been working on getting Intrepid to work, and during my labors, I messed up the folder that holds the evolution settings, namely .gconf. I still have my .evolution folder, which has all of my mail, contacts, tasks, etc, but I can't get at it because I lost the settings in .gconf.

Now whenever I start evolution, it wants to set up from scratch as if I don't have any mail accounts. Is there any way to remap these settings? I had about six accounts, and I have about 600 contacts that I'd love to be able to access again.

---

### Post by ajgreeny on 2008-11-14
If you can get a working .gconf folder in your home folder, you can easily copy the old (assuming you still have it) .gconf/apps/evolution folder back to the new .gconf.  This sounds as if it could be a good, and I hope not too late lesson, in backing up your /home often enough to avoid such situations.

---

### Post by mlissner on 2008-11-14
Thanks for the reply. I just figured this out. I had a backup that I had exported from the evolution backup tool that was pretty old, but had all the settings. 

I used that to recreate all the correct settings in gconf, and then I deleted the newly created .evolution file, and replaced it with my old one. Worked like a charm, though I'm officially in the process of reinstalling the OS - Intrepid did too much damage.

---

