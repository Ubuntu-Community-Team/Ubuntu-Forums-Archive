---
title: "Symbolic links Vs Hard links"
date: 2008-09-08
forum: General Help
---

### Post by sulekha on 2008-09-08
Hi all,

AFAIK the following are the differences between symbolic links and
hard links
Is there any other point which I have missed ?

symbolic link

when you try to open a symbolic link which points to a file or change
to one that points to a directory,the command you run acts on the file
or directory that is the target of that link.the target has its own
permissions and ownership that you cannot see from the symbolic link.

The symbolic link can exist on a different disk partition than the
target.

Hard link

It can only be used on files(not directories) and is basically a way
of giving multiple names to the same physical file.

hard links that point to that single physical file must be on the same
partition as the orginal target file.

The files are hard links if they have the same inode number.

---

