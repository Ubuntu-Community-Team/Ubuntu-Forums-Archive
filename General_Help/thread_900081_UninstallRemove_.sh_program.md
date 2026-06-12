---
title: "Uninstall/Remove .sh program"
date: 2008-08-25
forum: General Help
---

### Post by Shiskimalii on 2008-08-25
I have recently installed a .sh file (penumbra overture demo) and would now like to uninstall it but cannot figure out how. Any ideas?

---

### Post by wannadumpwindows on 2008-08-25
You should just be able to delete it. ".sh" files are just text files. It's not "installed" in the usual sense of the word.

---

### Post by Shiskimalii on 2008-08-25
Perhaps I should elaborate a little more... I already deleted the file but I want to uninstall the game

---

### Post by niccholaspage on 2008-08-25
Hm...Do you know where the game's directory is?

---

### Post by wannadumpwindows on 2008-08-25
There's usually another script in the directory that you can run to remove a program, just like you installed it.

The name will most likely have "remove" or "un-install" in it.

---

### Post by Shiskimalii on 2008-08-25
/usr/local/games

If you just want me to delete the directory I can but a little help removing the menu item would be appreciated.

---

### Post by wannadumpwindows on 2008-08-25
Right click your start button, then just click "edit menus". Delete the entry you don't want.

---

### Post by Shiskimalii on 2008-08-25
Wow that was so simple yet not because of all my windows time. Thanks... and now perhaps for a new thread to figure out my graphics problem

Oops didn't even see your post about the remove script but I've already looked and do not see one so I'll just delete the whole folder.

---

### Post by sameerds on 2008-08-25
> **Shiskimalii said:**
> /usr/local/games

If you just want me to delete the directory I can but a little help removing the menu item would be appreciated.

If the game also came with an uninstall script, that is obviously the first thing to try. If not, it can get a bit complicated, unless you are already familiar with shell scripts. That installer script is actually a series of commands that puts files in various places. You can go through them to figure out what are the files it copied. But there could be commands that implicitly copy files to system locations. The final place where the copy was placed would not be present in that script, so you might end up having to read the manpages for some of these commands.

---

### Post by wannadumpwindows on 2008-08-25
Yeah, and unless you have nothing else using that directory, completely deleting it might be a bad idea. Even if nothing else is using it, it could still cause headaches later.

There's most likely an un-install script, that'd be your best bet.

---

### Post by Shiskimalii on 2008-08-25
I had that thought it would be bad in the back of my head but I see no uninstall script and I don't want to go through the headache of finding all of that so unless you've got any easy suggestions I think I'll just leave it because I have plenty of memory. I just wanted to get rid of it.

---

### Post by sameerds on 2008-08-25
> **Shiskimalii said:**
> I had that thought it would be bad in the back of my head but I see no uninstall script and I don't want to go through the headache of finding all of that so unless you've got any easy suggestions I think I'll just leave it because I have plenty of memory. I just wanted to get rid of it.

Good call. If you feel up to it, do try to bug the original distributors to provide an uninstall script!

---

### Post by wannadumpwindows on 2008-08-25
There's a thread in the support forums for removal of the linux demo. Go take a look:

[http://frictionalgames.com/forum/showthread.php?tid=1170]("http://frictionalgames.com/forum/showthread.php?tid=1170")

---

### Post by Shiskimalii on 2008-08-25
> **sameerds said:**
> Good call. If you feel up to it, do try to bug the original distributors to provide an uninstall script!

Oh I am because that is just wrong.

---

### Post by Shiskimalii on 2008-08-25
> **sameerds said:**
> Good call. If you feel up to it, do try to bug the original distributors to provide an uninstall script!

Oh I am because that is just wrong.

> **wannadumpwindows said:**
> There's a thread in the support forums for removal of the linux demo. Go take a look:

[http://frictionalgames.com/forum/showthread.php?tid=1170]("http://frictionalgames.com/forum/showthread.php?tid=1170")

Huh... and I spent a long time searching the web for a solution. Guess I'll have to work on my searching skills.

Edit: That solution has me deleting the folders that I installed it to which we decided earlier not to do. Guess I'll delete those now.

*deleting that accidental post above would be helpful*

---

### Post by wannadumpwindows on 2008-08-25
> **Shiskimalii said:**
> Oh I am because that is just wrong.



Huh... and I spent a long time searching the web for a solution. Guess I'll have to work on my searching skills.

Edit: That solution has me deleting the folders that I installed it to which we decided earlier not to do. Guess I'll delete those now.

*deleting that accidental post above would be helpful*

Not the same files, you suggested deleting an entire directory before: "/usr/lib/games".

This is telling you to delete a couple directories in your home directory which is what "~/" means.

---

