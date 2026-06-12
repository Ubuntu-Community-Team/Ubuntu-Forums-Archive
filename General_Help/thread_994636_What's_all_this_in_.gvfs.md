---
title: "What's all this in .gvfs?"
date: 2008-11-26
forum: General Help
---

### Post by loonsailor on 2008-11-26
I was trying to backup my home directory ( rsync -avr ~ canseco::backup/aparicio) and was surprised to see LOTS of files being backed up from ~/.gvfs.  The files (85GB, according to du) were all files that live in the same directory on the nas that I'm backing up to.  What are they doing in a hidden file in my home directory?

It seems like these files are somehow mirrored or something, from the server, which causes them to be backed up as duplicates on the same server.

Huh?

I do see that gvfs is the "gnome virtual file system" but I still don't understand what's going on here.  I had, earlier, opened the gnome file browser to look at the nas directory and watch what's going on.  Could that be causing this?  At this point, can I safely delete .gvfs/* and try the backup again without the file browser running?

Thanks for any help.

---

### Post by jpkotta on 2008-11-28
I don't use Gnome.  I wouldn't delete it, but just add an exclude to your backup command.

---

