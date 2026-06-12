---
title: "&quot;Shared Documents&quot; Equivalent"
date: 2008-08-01
forum: General Help
---

### Post by Roger Mudd on 2008-08-01
The one thing that's keeping me from switching completely to Linux is my ability to easily share files and directories among users of a single machine.
I'm looking for something similar to "Shared Documents" in XP, where all users have unfettered access to files therein. In practice, I'd like to give other users within my household access to directories of photos, music, videos and other documents.
I've looked into group and user permissions as well as ACL and umask only to discover that there is no panacea. Each of those options leaves something to be desired. I believe others have come to the same [conclusion]("http://brainstorm.ubuntu.com/idea/3916/").
I understand the security implications of sharing files and can comprehend why such a solution is not implemented by default, but I'm disappointed that there is no easy way to set this up easily after the fact.
If you have any fail-proof solutions I'd love to hear them or if you know of a well-written guide that I haven't been able to find please let it be know.

---

### Post by ModelM on 2008-08-01
Most of the problems people run into when trying to do this stem from creating the shared folder in a privileged area like their home directory.

Create a shared directory in the root directory which is world read/writeable and put your shared stuff there. If you want this shared directory to appear on your desktop, create a link on your desktop pointing to it.

There are FTP servers all over the planet running *nix operating systems which have publicly accessible folders called, oddly enough, "pub". The files within can be shared between users, the outside world via FTP, anyone. But if you look at the directory structure you'll see that the "pub" directory is not within the privileged /home directory tree.

What this won't do for you, however, is automatically modify permissions on a file you put there.

Let's say you create a document "weeks.menu.txt" detailing the dinner menu for each day next week. You put this document into the shared /pub (for this example) directory. The rest of the family can read it, but little Jimmy won't be able to delete "broccoli" for Tuesday night unless you manually change the permissions on the file to allow others write permission. I've never looked into this, there may be a way to do it automatically.

---

### Post by Roger Mudd on 2008-08-01
Thanks for the quick response ModelM. The "problem" seems to boil down to permissions. Sharing files and directories seems to be easy enough. Easily modifying the permissions and having them remain persistent and recursive appears to be the sticking point. Perhaps this request flies in the face of *nix security/permissions theory, but it's a feature that interests many users (see link in my initial post).
I belive OS X has worked around this with their /Users/Shared directory. OS X, from what I've read, is grounded in *nix, so apparently it can be done.

---

### Post by Roger Mudd on 2008-08-05
Yes, in bad taste I'm responding to myself ;-)
Quick question -- how reliable is the NTFS driver? Would using a second internal hard drive formatted as NTFS be a ridiculously circuitous yet effective method of achieving the "shared directory" I seek? Or is the driver not yet stable and will I run the risk of corrupting my data?

---

### Post by mb_webguy on 2008-08-05
The current NTFS driver used by both Gutsy and Hardy is very solid.  I run a dual-boot system with Hardy and Vista, and have all of my user data on an NTFS partition so that it can be accessed by both OSes.  I have fstab set to mount the NTFS partition with umask=000 (giving full read/write/execute permissions for all users).  Since NTFS can't deal with Linux-style permissions, every file on that partition automatically gets full read/write/execute permissions as well.

If my system were a multi-user system, I'd have the NTFS partition mounted with umask=007 or something similar, with a special user group that has access to that partition.

Of course, given the prominence of /pub directories, I'm sure there's a way of automatically changing the permissions of any files placed there.  I can think of a couple of shoestring methods off the top of my head, but I think there's probably a "right" way to do it that I can't think of right now...

One thing to keep in mind is that Linux was developed from the start as a multi-user system, whereas Windows was developed as a single-user system.  Therefore, when it comes to things involving multiple users, if Windows can do it, then Linux can probably do it *better*.

---

