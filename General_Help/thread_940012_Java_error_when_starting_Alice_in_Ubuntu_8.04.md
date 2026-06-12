---
title: "Java error when starting Alice in Ubuntu 8.04"
date: 2008-10-06
forum: General Help
---

### Post by (Corndog) on 2008-10-06
When i try to run a program called alice (alice.org) i get the error:

```

evan@evan-laptop:~/Desktop/Alice/Required$ ./run-alice
attempting to register mp3 capability... 
Registered succesfully
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at edu.cmu.cs.stage3.alice.authoringtool.JAlice.configInit(JAlice.java:258)
   at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:117)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...2 more

```

Any idea why?

---

### Post by EvilMarshmallow on 2008-10-06
Looks like you're missing a library.

What java are you using?  I found that the default java package for ubuntu didn't work, I had to apt-get install sun-java6-bin and then update-alternatives and select the Sun Java.

Alice is a fickle program (I'm teaching a course in it this fall, as a matter of fact) and doesn't play nice with 64-bit, either, from what I've seen.

---

### Post by (Corndog) on 2008-10-06
Thanks :) worked like a charm :)

---

### Post by Wild_Doogy on 2008-10-17
I am working on the same thing:
I downloaded Alice as "Alice-2.0.0.tar.gz"
and I extracted it (for lack of knowing how to get it to install. might be part of the problem.....)

I apt-got  (past tense of apt-get)  sun-java6-bin and it installed alright, but, no good, I still get the same error. 

I also tried running the (I think) launcher script in a few different ways.
(paste into terminal,  open as a terminal script)
I get the same error as (cant find his name now). I don't know, but it looks like i have to do the update-alternatives, but when I run it there isn't a list of packages to update, and when I try to pass java to it, it says it doesn't like arguments.

help anyone? :confused: :(

Wild_Doogy

By the way: first post.

I fixed a friends comp that was VERY virus and bad thing infested, by installing Ubuntu.  works like a charm, but they now have my secondary hardrive and to get my computer to boot I had to reinstall Ubuntu which I had only played around with. Now my XP isn't working buts thats OK, I REALLY like Ubuntu.

---

### Post by ShelJ on 2009-01-03
Hi,

Is there a way to get it running on 64 architecture?  I'm taking a course on it this semester, and would like to be able to use it at home, however when I try to run it I get the following error:

```

java.lang.UnsatisfiedLinkError: /home/sheldon/Alice/Required/jogl/lib/linux-
i586/libjogl_drihack.so: /home/sheldon/Alice/Required/jogl/lib/linux-
i586/libjogl_drihack.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)

```This is not a huge problem, as I am getting a new Macbook soon, but it would be nice to have it running on both Linux and Mac.

Thanks,
ShelJ

---

