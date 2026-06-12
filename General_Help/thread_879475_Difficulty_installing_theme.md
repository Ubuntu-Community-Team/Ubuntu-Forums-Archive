---
title: "Difficulty installing theme"
date: 2008-08-04
forum: General Help
---

### Post by jaroon on 2008-08-04
I just installed Ubuntu 8.04.1 after watching youtube videos of the effects and I've started migrating to linux distros in my labs, so I figured I'd try it out on my computer.
Found this theme today and wanted to try it out, no clue how to do that.  The link is [http://www.gnome-look.org/content/show.php?content=79849&forumpage=0]("http://www.gnome-look.org/content/show.php?content=79849&forumpage=0") and it says to just drop the folders where they go.  I have no idea where these folders are, done a few searches and got nothing.  Can you guys look over this and tell me what I'm doing wrong.

---

### Post by Krydahl on 2008-08-04
~/ means your home directory. So, if your username is fred, ~/ is the same as /home/fred.

Any file or directory that begins with a dot (like .themes etc) is hidden by default. This means it won't show up when doing standard list commands or using nautilus.

If you're looking for these directories using nautilus, hit CTRL H and you'll see them (or tick the box in nautilus's preferences). If you're in a terminal, there are a number of ls options that will show hidden files, try "ls -al".

---

### Post by jaroon on 2008-08-04
Next question, how do i get fluxbox, did a few google searches and found nothing but outdated versions or incompatible versions.

edit: found a sudo command for it, and i'm not a fan, thanks for the help with the folders though

---

### Post by northern lights on 2008-08-04
It is generally advisable to have one thread per issue.

As for the first:
Download the theme from gnome-look > open the folder you downloaded to > navigate to "System > Preferences > Appearance" > drop the theme from the nautilus window into the Appearance one. Done.

As for the second:
```
sudo apt-get install fluxbox
```

---

