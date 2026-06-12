---
title: "[SOLVED] Weird Folder / File Problem Hardy"
date: 2008-09-19
forum: General Help
---

### Post by joeyknuccione on 2008-09-19
I placed a bunch of music files into my music folder, then started placing these files into folders according to artist. So I get real close to being done and all of a sudden the folder seems locked up. It still shows as having files in it, but when I open the folder I can't see any files or folders, and I have to force quit in order to get out of the folder.

What is up? Preciate any help.

---

### Post by spibou on 2008-09-19
When you say "open the folder" etc. which programme are you using? Do you know how to use the command line? If yes go to the command line, go the directory (folder) and do ls. Are the files there? What do you mean "force quit"?

---

### Post by joeyknuccione on 2008-09-19
> **spibou said:**
> When you say "open the folder" etc. which programme are you using? Do you know how to use the command line? If yes go to the command line, go the directory (folder) and do ls. Are the files there? What do you mean "force quit"?

I guess it's gnome I use to view these folders. 

using the command line and 'ls' does display the files within the folder.

"Force Quite" is when the folder is open, and hanging up, then I hit the X in the upper right, and a moment later I get:
 
   File browser is not responding.
   _____wait_________force quit

---

### Post by joeyknuccione on 2008-09-19
bump

---

### Post by joeyknuccione on 2008-09-19
bump

---

### Post by jerome1232 on 2008-09-19
I don't have a soloution but I can clear a few things up for you

Your are using Nautilus, that is the default file manager for gnome (for KDE it's konquer, Windows it's Windows Explorer)

So it sounds like Nautilus is just freezing on you, since the command 'ls' shows the files there you at least know they are fine. Does it only happen when you open this folder and is it repeatable everytime you open that folder?

---

### Post by joeyknuccione on 2008-09-19
> **jerome1232 said:**
> I don't have a solouting but I can clear a few things up for you

Your are using Nautilus, that is the default file manager for gnome (for KDE it's konquer, Windows it's Windows Explorer)

So it sounds like Nautilus is just freezing on you, since the command 'ls' shows the files there you at least know they are fine. Does it only happen when you open this folder and is it repeatable everytime you open that folder?

Thanks. Yeah, its just the one folder acting up. I hate to lose the contents though, so I'm hoping I can get it sorted out.

---

### Post by jerome1232 on 2008-09-19
You might want to launch nautilus from a command line and see what errors it spits out when you try and open that folder.

---

### Post by joeyknuccione on 2008-09-19
> **jerome1232 said:**
> You might want to launch nautilus from a command line and see what errors it spits out when you try and open that folder.

Got the idea to copy the folders to a new location. Worked, all good to go.

Preciate your help

---

