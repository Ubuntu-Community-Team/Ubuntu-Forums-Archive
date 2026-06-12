---
title: "Where should I put this program?"
date: 2008-09-04
forum: General Help
---

### Post by gamelord12 on 2008-09-04
I got the newest version of Eclipse (not found in the repositories) which is merely extracted and then placed anywhere before it is run.  However, when it comes to my computer, I'm kind of a neat freak.  Where should I put it?  Most other programs put their executables in /usr/bin, right?  Should I put the executable there and then put the rest of the files somewhere else?  I'm kind of a Linux noob.

---

### Post by unoodles on 2008-09-04
Either run it from your home dir, or put it in /usr/local/bin

---

### Post by gamelord12 on 2008-09-04
I think I read once that all the commands run from a Terminal or what have you are read from the executables in those specific directories.  Will putting it in that local directory make it so that I can't launch Eclipse by typing in "eclipse" in a command line?

---

### Post by gamelord12 on 2008-09-16
If I put the whole eclipse folder in /usr/bin, I can't launch it with the command "eclipse", nor can I do that by copying just the executable outside of the folder into /usr/bin.  How can I get the command eclipse to launch this version of the program that's not in the repositories?

---

### Post by Kilnr on 2008-09-16
I tend to put stuff like that in /opt (as per the [Filesystem Hierarchy Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)). Just put the Eclipse folder there (or anywhere else you like, really) and make a link in /usr/bin/ that points to the executable with
```
sudo ln -s /path/to/eclipse/executable /usr/bin/eclipse
```

---

