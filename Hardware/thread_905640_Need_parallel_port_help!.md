---
title: "Need parallel port help!"
date: 2008-08-30
forum: Hardware
---

### Post by chriscross93 on 2008-08-30
I need to give a program (parashell) direct access to my parallel port. I have been searching/working on it all day, but to no avail. Any help or suggestions would be greatly appreciated!

---

### Post by cariboo on 2008-08-30
Didn't i answer your question in the other forum you posted this question in?

Jim

---

### Post by linux_tech on 2008-08-30
There is more than one way to control parallel ports in linux. Can you elaborate more on what you wish to achieve, then maybe it will be easier to get more assistance.

Parallel port controlling in Linux; download the source-
[http://www.eee.deu.edu.tr/~ozkurt/comporg/ekonomi/hw2006/selen2/inlinux.htm](http://www.eee.deu.edu.tr/~ozkurt/comporg/ekonomi/hw2006/selen2/inlinux.htm)
Save the source code to file lpt_test.c then
```
gcc -O lpt_test.c -o lpt_test
```
see rest of instructions to change permissions, then recompile and run program.

---

### Post by Sef on 2008-08-30
> cariboo907
Didn't i answer your question in the other forum you posted this question in?

Yes, you did.  Thank you for spotting that.  If you spot another double thread, just click on the report button on the bottom left.

Locked. [Duplicate Post]("http://ubuntuforums.org/showthread.php?t=905637").

---

