---
title: "How do I transfer root partition to another partition?"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by Navyblue on 2005-12-21
Hi guys,

I am trying to transfer my Kubuntu installation from one harddisk to another hardisk. I have no problem for all partion except for the one holding the root directory.

I tried to copy the whole partition over with Konqueror. The source is only less than a GB but the resultant size would become a few GB. I have excluded the directories that are in their own partition. My wild guess  is the problem lies at the unique directory liek /dev, /proc or the likes. What is the correct way to copy this partition?

The source filesystem is ext3 and the the target filesystem is reiserfs. So "dd" command doesn't work here as it would turn the target partition into a ext3 as well.

Thanks for reading.

---

### Post by psusi on 2005-12-21
The last time I did this I used tar.  Something like this:

tar cfl - / | (cd /target ; tar xf -)

The l flag tells tar to only copy that filesystem, and not others that are mounted under it.  Tar also will ignore unix domain sockets ( since copying them does not make any sense ) and preserve permissions.  

You will of course, need to run this as root, so prefix it with a sudo if you aren't already in a root shell.

---

### Post by Navyblue on 2005-12-21
Thanks for your prompt response. If I wanted to copy everything except "/home" "/tmp" and "/usr", what would the command look like?

Edit:

When I typed "sudo tar cfl - / | (cd /media/linux ; tar xf -) ". I get this:

```
tar: xxx: Cannot open: No such file or directory
```

/media/linux is the target partition or directory.
xxx denotes the path of the individual files in the filesystem.

What am I missing here?


Editted again:

I found out that "sudo" doesn't do the trick here,  "su" is needed to perform the trick

However, the source parttition is about 800 MB and the target partition is only about 400 MB.

---

### Post by psusi on 2005-12-21
You can exclude specific paths with the --exclude= option to tar.

---

### Post by Navyblue on 2005-12-22
No luck yet, the resultant total file size is still different from that of the source's.

---

### Post by Navyblue on 2006-01-05
Anyone can help?

The resultant total file size is still different from that of the source's.

And the most important thing is it can't boot. It starts to display "fail" from the step  "initialising random number generator" and hung there a couple of steps after.

---

