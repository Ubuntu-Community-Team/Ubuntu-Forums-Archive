---
title: "Can't read &quot;c:&lt;backup&lt;&quot; directory"
date: 2009-04-03
forum: Hardware
---

### Post by stephieb on 2009-04-03
We have just installed Ubuntu 8.10 on our PC and had previously made a backup of our Windows C: drive onto our second hard disk, while running from the Ubuntu Live CD (before installing Ubuntu onto the hard disk).

There were some other directories previously on the second hard disk, which we can still read in Ubuntu, but the backup we have made does not seem to be readable (along with another directory which was already present).

The backup folder is:

/media/New Volume/c:<backup<

(This includes the colon and the left angle brackets. However, when the folder was created the name was "c: backup" (with a space between the colon and backup))

The folder seems to be completely inaccessible, we cannot list the contents of it using 'ls' and it does not show up in the GNOME file manager.

When listing the files in the parent directory, the folder shows as:

d????????? ? ?    ?           ?                ? c:<backup<

(ie, with no file permission, ownership, size or timestamp information)

When trying to list the contents of the folder (or run other commands, such as 'cd' or 'file'), we get errors such as the following:

ls: cannot access c:<backup<: Input/output error


Does anybody have any ideas on how we can try to recover the files from this folder?

Thanks for any help you can provide!

---

