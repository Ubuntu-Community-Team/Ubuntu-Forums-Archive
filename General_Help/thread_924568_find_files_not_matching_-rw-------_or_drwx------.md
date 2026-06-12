---
title: "find files not matching -rw------- or drwx------"
date: 2008-09-19
forum: General Help
---

### Post by botfish on 2008-09-19
I would like to search my home directory for:

All files with permissions that are NOT -rw-------
and
All directories that with permissions that are not drwx------

I think find can do it with the -perm option but I am having trouble understanding:

"... find allows you to specify a pattern that can be bit-wise ANDed with the permissions of the file. Simply put a minus sign before the octal value."

This is as far as I've got:

find . -type f -perm -[some_pattern_here] -print
find . -type d -perm -[some_pattern_here] -print

Thanks for any help

---

### Post by stickmangumby on 2008-09-19
Good work getting that far. 

I think the following is what you're after:

// Find any file that is executable by user, or accessible at all by group or other
find . -type f -perm /u=x -perm /g=rwx -perm /o=rwx -print

// Find any directory that is accessible at all by group or other
find . -type f -perm /g=rwx -perm /o=rwx -print

The / before the description of permissions is used to match any of the following permissions, as opposed to all or none of them.

---

