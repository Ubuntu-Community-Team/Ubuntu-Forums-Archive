---
title: "[SOLVED] Desktop is Home directory. How to recover?"
date: 2008-10-19
forum: General Help
---

### Post by Pa100ka on 2008-10-19
Hi,

I made a stupid mistake. I had a few downloaded files on my desktop. I created a new directory (usapics) under my home directory. intending to move the files there.

By mistake, instead of doing mv * $HOME/usapics from $HOME/Desktop, I ran the command from $HOME. So all that hidden stuff got moved, and I was greeted with the default mud-coloured desktop. Daft, eh?

I moved the files back, and everything is OK again, except that somehow Gnome now thinks that my desktop is /home/Pa100ka instead of /home/Pa100ka/Desktop. This means that bin, public, share, Documents, Pictures and so forth all show up as folders on my desktop (there's an empty folder called Desktop there too).

Can anyone help me recover from this?

Thanks,
Pa1ooka :confused:

---

### Post by loomsen on 2008-10-19
Type

```

gconf-editor

```

Search for the key:

Apps  -->  nautilus --> preferences  --> and uncheck desktop is home dir :)

---

### Post by Pa100ka on 2008-10-19
> **loomsen said:**
> Type

```

gconf-editor

```

Search for the key:

Apps  -->  nautilus --> preferences  --> and uncheck desktop is home dir :)

Many thanks for the reply. Indeed, that's what the configuration editor says it does. Unfortunately it was already unchecked. I tried checking it and unchecking it again (with restarts in between to try to be absolutely sure). Neither seems to make any difference whatever. I am really puzzled now.

Edit: Found the answer here: [http://ubuntuforums.org/showthread.php?t=762164](http://ubuntuforums.org/showthread.php?t=762164). Many thanks to laffinet, and to loomsen

Thanks,
Pa100ka

---

