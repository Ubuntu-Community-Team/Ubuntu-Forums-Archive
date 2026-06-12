---
title: "Output when creating a tarball"
date: 2008-11-18
forum: General Help
---

### Post by eludlow on 2008-11-18
I have a script which, through a cronjob, creates a tarball of a mounted location.

I use the following:

```
tar czf backup.tgz /home/ed/mount
```

This works fine, but I always get:

> tar: Removing leading `/' from member names

mailed to my system mail account.

Is there any way to suppress this output?

Thanks,
Ed Ludlow

---

### Post by geirha on 2008-11-18
Warnings are usually printed to stderr. You can redirect stderr to somewhere else with
```
 
some command 2>> /path/to/some/file    # Appends the warnings and errors to a file
some command 2> /dev/null              # Sends the warnings and errors to oblivion

```

---

### Post by eludlow on 2008-11-18
Thanks.  So will that set the warnings for each command permanently?

If I were to run:

```

tar 2>> /home/ed/tarOutput

```

That woudl output all tar warnings to the file tarOutput?

How do you reset it back to default?

Thanks,
Ed

---

### Post by geirha on 2008-11-18
No, you need to add it to the actual command. In your case
```
tar czf backup.tgz /home/ed/mount 2>> /home/ed/tarOutput
```
If you have a new tar command after that one, without 2>> ... behind, then the warnings will be printed to stderr as usual.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

---

### Post by eludlow on 2008-11-18
Thanks a lot **geirah** - excellent howto :)

Ed

---

