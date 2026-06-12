---
title: "Program/File size on disk"
date: 2013-08-27
forum: Hardware
---

### Post by angel mike on 2013-08-27
How can I find how much disk space individual programs like Firefox and also files are taking up ?

---

### Post by bkline on 2013-08-27
There isn't a simple answer to the general question, because in addition to the space taken up by the program files at the time a program is installed, over time the program as it runs will store additional information.  In the case of Firefox, those files are likely as time goes on to take up much more space than the program itself.

For a more specific answer, tailored to Firefox, you can run

$ du -sh ~/.mozilla/firefox

to get an idea of what's been saved by Firefox over time.

If you back off from the requirement that you get specific numbers for each individual program, you might want to try playing around with the du and df commands.  The first tells you how much space is taken up by sections of the file systems, and df tells you how much space is free (and in use) by each of the file systems.

$ man du

and

$ man df

to find out more.

For example:

$ sudo du -sh /*

will tell you how much space is taken up by each of the major directories in the root filesystem.

---

### Post by Jonathan_Birk on 2013-08-27
You can also check out ncdu which is similar to du with a more "graphic" user interface.

---

