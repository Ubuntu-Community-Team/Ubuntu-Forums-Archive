---
title: "Cleaning out my Music folder"
date: 2008-08-12
forum: General Help
---

### Post by sporkubus on 2008-08-12
I did quite a bit of searching but couldn't find a way to do this that didn't involve a lot of work or that worked properly for me. I have a huge music collection but after organizing my collection with Amarok I now have a ton of empty and almost-empty folders (some have jpgs or configuration files from Windows). What I'd like to do is somehow delete all the folders under a certain size (say, 1 megabyte) automatically. I found a thread about how to do this with the terminal:

[http://ubuntuforums.org/showthread.php?t=646494&highlight=delete+empty+folders](http://ubuntuforums.org/showthread.php?t=646494&highlight=delete+empty+folders)

but I tried it and it didn't work for me, even with some tweaking.

---

### Post by pytheas22 on 2008-08-12
You can use the command-line, but perhaps an even easier way would be to open your music folder in Nautilus, and then choose View>Arrange Items By>Size.  Then all of the empty and near-empty folders should be at the top, and you can delete them.

If that doesn't work for you, tell us exactly what went wrong when you tried doing it on the CLI and maybe we can figure out how to make it work.

---

### Post by DeathOnJuice on 2008-08-12
> **pytheas22 said:**
> You can use the command-line, but perhaps an even easier way would be to open your music folder in Nautilus, and then choose View>Arrange Items By>Size.  Then all of the empty and near-empty folders should be at the top, and you can delete them.

If that doesn't work for you, tell us exactly what went wrong when you tried doing it on the CLI and maybe we can figure out how to make it work.

I'm not sure; it sometimes reports not the size of the contents of the folder, but the size of the folder itself (I assume. It seems odd that folders should have sizes, but I haven't been able to find any other explanation). I'm not sure if Nautilus sorts by contents or this, so make sure before you delete everything.

---

### Post by mb_webguy on 2008-08-12
Try KDirStat ("sudo apt-get install kdirstat").  It's a graphical disk usage utility that is quite a bit better than Ubuntu's default Baobab.  It makes it very easy to identify and manage files by size.

---

### Post by sporkubus on 2008-08-13
This is great, except it doesn't let me select multiple folders for deletion... I have literally hundreds of folders that need to be deleted, so it doesn't really make sense to delete them one-by-one.

---

### Post by mb_webguy on 2008-08-14
Ah, sorry.  I've never noticed that before.  I'm usually looking for the biggest files, not the smallest, so I don't guess I've ever needed to select more than one thing at a time...

---

