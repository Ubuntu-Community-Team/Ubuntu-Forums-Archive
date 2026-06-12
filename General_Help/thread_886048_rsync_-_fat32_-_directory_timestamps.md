---
title: "rsync - fat32 - directory timestamps"
date: 2008-08-10
forum: General Help
---

### Post by poorbadger on 2008-08-10
First off, I've been searching around for several hours trying to find a solution to this issue but haven't come up with anything that meets my parameters so far.  I think I'm going to have to try a different approach but I wanted to ask the forum first.

I've got 250GB or so worth of [FLAC]("http://flac.sourceforge.net/features.html") files I'd like to back up regularly to a USB drive.

The Ubuntu box hosting the files is 7.10 and formatted EXT3.  I've got a second drive in there that mirrors the files and is only mounted when backing up via rsync - it's EXT3 as well.  The USB drive is FAT32 for compatibility with Windows machines (I'm aware there are EXT3 drivers for Windows but don't want to install that on friend's machines - enough of a hassle to get them to install something that will play FLAC or encode FLAC>MP3).

Everything seems to work fine from EXT3 to EXT3.  When going from EXT3 to FAT32, directory modified dates are the time of the operation versus the modified date of the source directories.  Individual files at the root or within the subdirectories do have modified dates that match the source

The rsync command I'm using is...

```
sudo rsync -rout --verbose --progress /src /dest
```

-r    recurse into directories
-o    preserve owner (super-user only)
-u    skip files that are newer on the receiver
-t    preserve modification times

The first time through everything works fine.
Subsequent times through all files are copied - not just new or changed files.

Options considered and discarded:
Use checksum comparison (-c).  Not feasible as it would take way too long.
Use --no switch w/ -O (omit directories from time preservation).  It almost seems like it's using the -O switch and I thought explictly asking it not to might help.  --no-0 results in an error and rsync doesn't run
use --size-only switch for comparison.  This would end up failing to copy modified files when tags are changed (e.g. "Rock" to "Punk" to "Jazz" - all 4 characters thus same filesize)

Interestingly, copying directories/files from EXT3>FAT32 using ```
cp -a /src /dest
``` sometimes gives you the correct modified date and sometimes doesn't.  I haven't tested this enough to come up with a pattern but in my test of copying a directory with two subdirectories (with files inside them) the directory and the first subdirectory copied had the correct modifed date - the second subdirectory had a modified date as of the time of operation.

So that's a bit long-winded but hopefully it helps someone out along the way.

In summary:
I'd like to use FAT32 for easy Windows compatibility on my machine and friend's machines.
I'd like all directories and subdirectories to mirror the modified date of the source.
I don't want all 250GB worth of files copied every time.
I've ruled out checksum comparison due to the overhead (although this may end up taking less time than a full copy - I haven't let it run the whole way through).
I don't want to trust --size-only comparison as it can lead to files not being backed up when they should be.

The key issue appears to be the modified date of directories/subdirectories.

Secondary question: Does anyone know if this works any better under NTFS?  I'd be willing to try that route but Gparted doesn't give NTFS as an option on USB drives and I just haven't had time to figure out how to do this and enable automount from the command line - if someone else has had success doing so, that would become a viable option.

If you have a completely different approach, I'd be happy to hear it.

Thanks!

---

### Post by goexplode on 2008-08-11
FAT filesystems have a different resolution time than ext3.

Try using the --modify-window=NUM option with rsync, where NUM is some number greater than zero.

According to the rsync manpage:

> --modify-window
When  comparing two timestamps, rsync treats the timestamps as being equal if they differ by no more than the modify-window value.  This is normally 0 (for an exact match), but you may find it useful to set  this  to  a larger  value  in  some situations.  In particular, when transferring to or from an MS Windows FAT filesystem (which represents times with a 2-second resolution), --modify-window=1 is useful (allowing times to differ by up to 1 second).

In your case, I would try something like:

```
sudo rsync -rout --verbose --progress **--modify-window=2** /src /dest
```

---

### Post by poorbadger on 2008-08-11
Awesome!  That seemed to do it.

I ran a dry run (-n) using the --itemize-changes switch and it listed the directories as well as 3 out of 8 files in my test directory.

After comparing those files in both the source & destination directories I noted that the destination (FAT32) files had even seconds (e.g. 11:00:02) for modified date while the source (EXT3) had odd (11:00:01).  Guess FAT32 likes everything all nice and even.

Anyway, after adding the ```
-modify-window=1 -n
``` switches rsync told me it just wanted to update the directories.  As I mentioned, after the initial run the directories modified date was the time of operation.  The second time through using --window-size=1, the directory modified dates were updated to the same dates as the source (w/in a second).  Third time through, it was content to do nothing - as it should be :)

For the archives, here's an [informative article]("http://www.osnews.com/story/9681/The_vfat_file_system_and_Linux/page1") about vfat & linux.

Thanks!

> **goexplode said:**
> FAT filesystems have a different resolution time than ext3.

Try using the --modify-window=NUM option with rsync, where NUM is some number greater than zero.

According to the rsync manpage:



In your case, I would try something like:

```
sudo rsync -rout --verbose --progress **--modify-window=2** /src /dest
```

---

### Post by goexplode on 2008-08-11
Glad it worked! :)

---

### Post by hyper_ch on 2008-08-11
why not making it ext3 and install ext2/3 drivers on windows? FAT32 is just so... hmmm... limited.

---

### Post by poorbadger on 2008-08-11
I don't mind doing that on my own machines but that's not always possible on every machine you might want to hook a USB device up to - lab/library machines, corporate software audits, etc.

I agree w/ you in principle but sometimes the least common denominator is what's called for.

> **hyper_ch said:**
> why not making it ext3 and install ext2/3 drivers on windows? FAT32 is just so... hmmm... limited.

---

### Post by Junkieman on 2008-08-25
Reading this topic will save me much trauma, after deciding to rsync my files onto a FAT32 device... Thanks!! :biggrin:

---

### Post by poorbadger on 2008-08-25
Good! That's what the archives are here for :)

Yeah - use the modify-window switch and expect the directories to sync back up the 2nd time through (not the contents of the dirs - just the timestamp of the dirs)

--modify-window
    When comparing two timestamps, rsync treats the timestamps as being equal if they differ by no more than the modify-window value. This is normally 0 (for an exact match), but you may find it useful to set this to a larger value in some situations. In particular, when transferring to or from an MS Windows FAT filesystem (which represents times with a 2-second resolution), --modify-window=1 is useful (allowing times to differ by up to 1 second). 

> **Junkieman said:**
> Reading this topic will save me much trauma, after deciding to rsync my files onto a FAT32 device... Thanks!! :biggrin:

---

