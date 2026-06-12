---
title: "Home Directory Dot File Clutter"
date: 2008-07-27
forum: General Help
---

### Post by amg on 2008-07-27
Hello,

I've become annoyed with my home directory lately, mainly the dozens of applications that store settings within it.

I know, I know, it's been a standard for centuries. I don't want to completely change that standard, just tweak it a little bit.

Besides, I don't want to tell distributions how to work, applications how to store/find stuff, or telling anyone how to do anything, **I want a choice.**

I don't know if this is possible, or even makes sense, I'm hypothesizing.

Is it possible to create a script/daemon to "watch" the home directory, and whenever an application looks for a file, this script/daemon steps in, and gives the contents of another directory?

So, when beagle looks for /home/ashley/.beagle/ This script/daemon steps in (much like a body guard) and gives beagle /home/ashley/.settings/.beagle/. With ".settings" being whatever/wherever I want.

I'm sure this would be confusing to implement, because how will the script/daemon tell the difference between me browsing the home directory, and beagle reading/creating/editing configuration files.

Basically, my skills are non-existent, so, help, please.

Any suggestions?

---

### Post by scragar on 2008-07-27
I don't know about that, but you don't have to see the invisible files if you don't want, and nothing stops you placing all your personal stuff in a sub folder or 2, just move the stuff you want to a sub directory, edit the bookmarks in the file manger so the places menu and save/open file menu are still right and see how you feel about that.

---

### Post by amg on 2008-07-27
I know I don't have to view them, but on occasion, I have to search through the hidden files for something I've hidden (for whatever reason).

To me, it makes sense to have my configuration in a subdirectory, not my personal files in a subdirectory.

Also, I feel like that could cause problems for other applications accessing my home directory, and then I have to select my "real one".

---

### Post by todlangweilig on 2008-07-27
Well I like the idea of putting those files in a .settings folder. I think it makes a lot of sense to do. I don't know if there are reasons for not doing so other than historical. Maybe someone out there can shed light on any potential problems.

I think it would be pretty confusing and challenging to implement however. I think the kernel handles file operations, so this is going to be more challenging that a simple shell script. Not only that, but as you said, how is it going to know the difference between you and a program accessing the config file? You could tell it to ignore the hidden files for nautilus and ls. Or have the file accessible if a program is on a white list of accepted programs. This gets into a lot of hard coding or config file work though. If you install a new program, and it wants to get to your .bash_history file for example, the program would have to be informed of this. 

So why not just create a directory called, for example, .myhiddenfiles . Then stick your files you want hidden in there. When you want to access them, ctrl-h in nautilus and go to that folder. When you don't want to see them anymore, ctrl-h again. If you can't keep the config files separate from your files, keep your files away from the config files. It seems to be a far easier solution.

---

### Post by dbera on 2008-07-28
> **amg said:**
> 
So, when beagle looks for /home/ashley/.beagle/ This script/daemon steps in (much like a body guard) and gives beagle /home/ashley/.settings/.beagle/. With ".settings" being whatever/wherever I want.

I dont have any general suggestion but for beagle, you can set
BEAGLE_STORAGE in .bashrc or .profile to whatever directory you want beagle to store its index in. Just make sure that directory is itself out of beagle's indexing path (i.e. its not in the homedirectory as a normal directory) otherwise there will be recursive indexing and who knows what can happen. beagle website also mentions are few other environment variables that you can use.

---

### Post by amg on 2008-07-28
@dbera:

I appreciate the help, and I'm sure some google query down the road will as well, but I was merely using beagle as an example.

But, again, thansk for the response.

@todlangweilig

I know it would be confusing to implement, just in the little knowledge I do have about this I can tell it would be confusing.

I guess I was hoping some very nice person would come along and get interested.

Speaking of such, I was looking for a place to go and, well, request someone to build this, for money.

The only places I could find seems shady.

---

