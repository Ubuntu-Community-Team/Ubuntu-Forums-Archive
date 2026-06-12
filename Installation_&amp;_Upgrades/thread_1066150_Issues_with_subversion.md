---
title: "Issues with subversion"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by j.daniel on 2009-02-10
Ladies & gentlemen,

  I upgraded to 8.10 from 8.04 a few weeks ago. In 8.04 I was using the supplied version of subversion without any problems (don't remember which version of svn it was though).

  However, to my great dismay, I now get error messages when I try to use subversion (v1.5). More specifically when I try for instance the command:

```
svnadmin hotcopy .svn .svn_backup
```

  I get the error message:

```
svnadmin: Can't set permissions on '.svn_backup/hooks/start-commit.tmpl.tmp': Not a directory
```

  When I use the command:

```
svn import mr/atomic/source/ file:///NAS/Programming/.svn/atomic/trunk/source -m "Initial load"
```

  I get the error message:

```
svn: Can't open file '/NAS/Programming/.svn/db/transactions/261-1.txn/props': Not a directory
```

  The repository resides on an external cifs mounted NAS. This setup has not changed. The only thing that have changed is that I have upgraded from 8.04 to 8.10 - including the svn version I presume? The commands listed above have not encountered these kinds of errors before. 

  Anyone have any clues?

  My last resort will be to revert back to 8.04.

Cheers!
/ Daniel

---

