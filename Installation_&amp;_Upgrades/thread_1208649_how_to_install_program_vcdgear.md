---
title: "how to install program vcdgear ?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by tonjaa on 2009-07-09
i try to download program "vcdgear"  save on Desktop file name is     " [COLOR=SeaGreen]vcdgear176-040415_linux.tar.gz[/COLOR] "
how i can install this file please guide me .

---

### Post by unlimitedz on 2009-07-09
First extract the files.  Open a terminal and go to the Desktop Directory.  Then run ```
tar -xzvf [COLOR=SeaGreen]vcdgear176-040415_linux.tar.gz[/COLOR]
```Then look around in the extracted directory for a README or INSTALL text file, follow those instructions.

---

### Post by Mark Phelps on 2009-07-09
Short answer is ... you don't ... "install it", that is.

Let me explain ...

What you downloaded is a compressed archive file which most likely contains the source code needed to build the executable.

The first thing you will need to do is uncompress the archive to see what's inside it.  You do that by opening a terminal and typing "sudo tar -xvfz <filename>"  where <filename> is replaced by the full name of the file you downloaded.

That will most probably create a directory (and possibly subdirectories as well) containing lots of source files, some scripts, and some text files.

So what you're really asking is how to build an executable from source in Linux ... which is a LOT of work and the hardest possible way to obtain an application.

If you've not done this before, you will need to install library packages, starting with build-essential.

Search this forum on "building executables" and you will find examples of how to proceed.

---

### Post by tonjaa on 2009-07-10
thank you for guide me it make me understand about compress file . 
i try to extract file save on Desk top folder name  " vcdgear"  in folder has file like this 
[COLOR=Sienna]
tonjaa@tonjaa-desktop:~/Desktop$ cd vcdgear
tonjaa@tonjaa-desktop:~/Desktop/vcdgear$ ls
[COLOR=Cyan]CDI[/COLOR]  [COLOR=Black]Changelog  Credits[/COLOR] [COLOR=YellowGreen] [COLOR=RoyalBlue]lang[/COLOR][/COLOR] [COLOR=YellowGreen] vcdgear[/COLOR]  [COLOR=Black]vcdgear.cfg[/COLOR]
tonjaa@tonjaa-desktop:~/Desktop/vcdgear$ [/COLOR]

what is correct command to install it?

---

### Post by erichgamba on 2010-05-22
You don't have to install vcdgear. It is a pre-compiled program

---

### Post by yessine on 2010-10-19
I know this is late, but you have to type:

```
./vcdgear
```

I hope it resolved the issue.

---

