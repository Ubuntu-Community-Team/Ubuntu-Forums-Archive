---
title: "Backup changing files with ext HDD"
date: 2008-08-11
forum: General Help
---

### Post by GabrielWolff on 2008-08-11
I have an ever growing collection of photos, which I both take, copy to my int. HDD and edit.

Once in a while I want to backup my collection to an ext. HDD.

I need to:
1) Copy newly added pictures from my int. to my ext. HDD
2) Change edited pitures on the ext. That is: if I already copied a picture to the ext HDD at a previous backup, but later ecited it (on my int HDD) I need the old file to be replaced with the edited one
3) NOT to erase files I might have deleted on my int. HDD. I need those files to stay on the ext. HDD

When I just copy/paste the Picture folder to the ext HDD it gives me different options, and I choose Merge. But that doesn't do 2) and I think it doesn't do any recursive copying anyway.

What's a good solution for that?

---

### Post by unutbu on 2008-08-11
If you want to copy everything in say ~/images to /media/externalHDD/images
I think the following command should work:
```

rsync --verbose  --progress --stats --compress --recursive --times --perms --links ~/images/* /media/externalHDD/images
```

Be sure to test the rsync command out on a small practice directory first just to be safe.
(This command was taken from [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/))

[list=1]
[*] rsync will copy newly added pictures
[*] rsync copies only the diffs of files that have actually changed -- in other words, it is smart enough to recognize when a file hasn't changed. And it will update when a file has changed -- as long as it has the same filename.
[*] If you don't run rsync with the --delete option, files in the target directory that do not correspond to files in the source directory will not be deleted.
[/list]

Type man rsync (or google "rsync") for more info.

---

### Post by GabrielWolff on 2008-08-11
> **unutbu said:**
> If you want to copy everything in say ~/images to /media/externalHDD/images
I think the following command should work:
```

rsync --verbose  --progress --stats --compress --recursive --times --perms --links ~/images/* /media/externalHDD/images
```

Be sure to test the rsync command out on a small practice directory first just to be safe.
(This command was taken from [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/))

[list=1]
[*] rsync will copy newly added pictures
[*] rsync copies only the diffs of files that have actually changed -- in other words, it is smart enough to recognize when a file hasn't changed. And it will update when a file has changed -- as long as it has the same filename.
[*] If you don't run rsync with the --delete option, files in the target directory that do not correspond to files in the source directory will not be deleted.
[/list]

Type man rsync (or google "rsync") for more info.

Sounds exactly whatI was looking for :)

Thanks!

---

### Post by GabrielWolff on 2008-08-13
> **unutbu said:**
> If you want to copy everything in say ~/images to /media/externalHDD/images
I think the following command should work:
```

rsync --verbose  --progress --stats --compress --recursive --times --perms --links ~/images/* /media/externalHDD/images
```

Be sure to test the rsync command out on a small practice directory first just to be safe.
(This command was taken from [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/))

[list=1]
[*] rsync will copy newly added pictures
[*] rsync copies only the diffs of files that have actually changed -- in other words, it is smart enough to recognize when a file hasn't changed. And it will update when a file has changed -- as long as it has the same filename.
[*] If you don't run rsync with the --delete option, files in the target directory that do not correspond to files in the source directory will not be deleted.
[/list]

Type man rsync (or google "rsync") for more info.

I copied my Pictures folder to the ext. HDD, then I made the following changes to the "original" folder on the int. HDD: I
- changed one picture, 
- deleted another one and 
- added a third one. 
Then I ran the script.

What happened was the following:
1) The whole directory was copied once more. That is: all my files were copied once again, even those I didn't touch.
2) It* did* delete on the ext. the files I deleted on the int. HDD

In other words: the script simply replaced the folder I added to the ext. HDD in the first place with the folder I had on my int. HDD.

Any chance you could show me what has to be changed?

---

### Post by GabrielWolff on 2008-08-13
Update: I found out why the deleted files got deleted on the ext. HDD as well and fixed it. I just had copied the files first to a different directory than the script did. So in the end I had two folders.

But still: rsync doesn't skip a single file, ignoring the same size and date, and copies all of them again. How come? I checked on their man pages, and it seems like it shouldn't...

Anyone?

---

### Post by unutbu on 2008-08-13
Hm. I tested the command I posted, and it seems to only copy files that have been modified or created, and it does not seem to delete files in the destination directory that are no longer present in the source directory.

There are many options for rsync -- perhaps for some reason I don't understand the options I suggested are not right for your situation.

One thing I just realized is that the --compress option is perhaps not right for you. Images do not compress well, so it is probably better to omit the --compress option.

Here is another command which may be better (actually, it should be about the same, but maybe it would not hurt to try):
```

rsync --archive ~/test/* ~/test-0
```

If this does not work for you, check that the timestamp on the files in the backup directory is the same as the timestamps in the source directory. If the timestamps differ, this may be why the files are all being transfered again.

PS: When I alter just one file, and then issue the rsync command, I get in the output:

```
Number of files: 168
Number of files transferred: 1              <-- Only 1 file was transferred
```

Is this how you are checking that all files are being transferred each time you run rsync?

PPS: Here is a nice little tutorial with example rsync commands and an explanation of common options: [http://www.sysresccd.org/Sysresccd-manual-en_Backup_and_transfer_your_data_using_rsync#-u.2C_--update:_skip_files_that_are_newer_on_the_receiver](http://www.sysresccd.org/Sysresccd-manual-en_Backup_and_transfer_your_data_using_rsync#-u.2C_--update:_skip_files_that_are_newer_on_the_receiver)

Sorry I can't answer your question directly. Hope this helps.

---

