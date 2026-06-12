---
title: "Deleted files are still here?"
date: 2005-11-11
forum: General Help
---

### Post by Master Magnus on 2005-11-11
Am I stupid or is this really hard?

I decided to leave windows completely for Ubuntu, and therefore I had to reformat the second drive. I moved the files from there to my master and it barerly just fit . I had a few gigs left when all files were copied. Then I reformatted drive 2 and copied the files back. When I later deleted the folder with all the back upped files on hard 1 they disappeared from vision, but I still only have those few gigs left. Help me!!! :( :confused:

---

### Post by Kyral on 2005-11-11
Empty the Trash?

---

### Post by Master Magnus on 2005-11-11
Yeah, ofcourse - I'm not that stupid :p As long as you meen the trash that you can access from the desktop. In windows there's a place where the files are saved even after deletion from the recycler, that's what I'm wondering over... If there's something like that in Ubuntu..?

---

### Post by Lambert on 2005-11-11
There is a hidden file for each user /home/<user>/.Trash This is the trashcan on the desktop.
When files are deleted from here they are gone.


run this command

```
du -h /home/<user> | less
``` 
and it will show you size of each folder recursively through out that directory.

You can change /home/<user> to any directory to see size.

---

### Post by Master Magnus on 2005-11-12
I can still not find it. Is there any tool like Diskdata for Linux? That was a good tool :(

---

### Post by Lambert on 2005-11-12
I'm not that familiar with diskdata but you can look at [COLOR=Blue][baobab]("http://www.marzocca.net/linux/baobab.html")[/COLOR]. It's in the repositories.

[COLOR=Blue][Screenshots]("http://www.marzocca.net/linux/bbshots.html")[/COLOR]

---

### Post by Master Magnus on 2005-11-13
Hm, I can't find it in: Applications > Add applications  -  Settings > Repositories. And when I'm only going to Applications > Add applications > Baobab this message comes up as description:

This program is not currently installable. It should be available in the "universe" section of the repository. Enable that section in the Repositories dialog in the Settings menu to install it.

But there's nothing in Settings > Repositories. Just CD, updates and security updates. :(

---

