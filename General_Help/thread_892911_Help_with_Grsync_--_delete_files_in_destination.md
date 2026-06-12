---
title: "Help with Grsync? -- delete files in destination"
date: 2008-08-17
forum: General Help
---

### Post by DaveH999 on 2008-08-17
I'm using Grsync to backup my hard drive via rsync, and one option isn't working for me.

I've checked the box that adds the argument "--delete."  My understanding of this is:

If file X is on my hard drive during backup A, it will appear on my backup. (this works fine)

If file X is NOT on my hard drive during my second backup, B, it will be deleted from my backup.

But file X is still appearing.  It's like files just keep piling into directories, even when the files no longer exist.

Is there maybe an option I need so that deletion happens on all levels of files and folders?

Thanks for any help!

---

### Post by bretto_40 on 2009-06-09
I'm having the exact same issue. Except, I'm 100% positive I tested this when I set it up and found that the files WERE being deleted from the destination after being removed from the source.

But now, I've noticed this morning after deleting a bunch of files from my one of my source directories that it now no longer deletes them from the destination. So same as you, it backs up ok still, but is not cleaning out old files on the destination.

I think it has something to do with NTFS, because I'm trying to backup from an EXT3 partition to an NTFS partition, and I'm guessing you're doing the same thing.

Problem is I don't know why or how to fix it!

Anyone any ideas? I have the correct options such as "Delete on Destination" enabled.... but no go.

---

### Post by bretto_40 on 2009-06-09
For anyone reading this I've just solved the problem.

Grsync was having some issues for quite some time re: a couple of hidden files/folders that for whatever reason it couldn't copy across (there were errors but I didn't understand them and they were non-critical files & folders anyway).

I never thought it was an issue because everything was still being backed up. So, if it was all getting backed up ok, why worry right?

Well, it turns out that those errors, while not stopping the backup of files, WAS stopping the deletion of files on the destination.

So to fix it I had a look at the error output at the end of a Grsync backup operation and had a look at the folders it was having problems with (again, nothing critical to me).

I copied the error output into a text file for ease of use, and then excluded those folders in Grsync by doing the following:

Go to the Advanced Option tab, and in the box at the bottom for additional options I entered the following (I'll use the actual command I put in as an example):

--exclude=.gfs --exclude=.config/banshee-1 --exclude=.config/menus

So this is telling Grsync to ignore the folders ".gfs", ".config/menus" and ".config/banshee-1". Note that your home directory is the default. I could have made the paths absolute by specifying /home/<username>/.gfs if I wanted to, but no need.

Also note as an example that the backup ignores the .config/menus and .config/banshee-1 folders, but backs up all of the other folders within .config, which is handy because they have config files for several apps.

I figure in the event of having to restore my backups after a major crash or something, I won't need the above excluded folders.

Anyway, once these were excluded the backup ran like a champ with no errors, and now my backup deletes obsolete files and folders on destination again!

Woohoo! :)

---

