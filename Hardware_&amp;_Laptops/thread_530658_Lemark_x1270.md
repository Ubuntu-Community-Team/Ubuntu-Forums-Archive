---
title: "Lemark x1270"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by MarkNewFeistyUser on 2007-08-20
I'm trying to follow a previous thread's instructions, [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714), but have failed miserably. I've downloaded the file and saved it in a folder called lexmark on my desktop. 

When I get to the command: tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # 
I get this message: 
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I've no idea what to do next. Any help is appreciated

Cheers

Mark

---

### Post by Stefano Fonzarelli on 2008-01-20
Seems like you are executing your command in the wrong directory. You need to be standing in the same directory as the tar-file is in!

Use CD and LS to navigate to the right directory and try again.

---

