---
title: "$DB shows \$DB in tab completion"
date: 2008-09-02
forum: General Help
---

### Post by gjzeus on 2008-09-02
First, I set variable like
```

export DB_DIR="/home/user/analysis/DB"

```
Then, I type
```

cd $D{press tab}
cd \$DB_DIR
bash: cd: $DB_DIR: No such file or directory

```

```

uname -a
Linux host 2.6.24-19-rt #1 SMP PREEMPT RT Thu Aug 21 02:08:03 UTC 2008 i686 GNU/Linux
bash --version
GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)

```

And I also turn on the default bash_completion. I didn't see the strange behaviour on redhat, fedora and opensuse(bash version is 2.05b), so I transfer the bash_completion file from redhat and to see what will happen. Unfortunately the problem is still there. 

Any idea for this one? 

Thanks in advance.

---

### Post by gjzeus on 2008-09-05
NO any response for 3 days.

---

### Post by gjzeus on 2008-09-05
I've already fixed it. Please ignore this thread

---

### Post by adriandown on 2008-10-07
gjzeus, if you're still around (or anyone else), could you please post your solution for those of us who haven't fixed it yet?

Thanks,
Adrian

---

### Post by adriandown on 2008-10-08
A post on a different forum [here]("http://www.linuxquestions.org/questions/linux-general-1/bash-auto-complete-of-environment-variables-613203/") address the same question and has a proposed solution.  However, following the instructions in the post did not fix the problem in Ubuntu 8.04.  The solution fixes the tab completion behavior for the immediate shell, but putting the commands in my .bash* files doesn't have any effect.

Any ideas what's going on here?  Thanks,
Adrian

---

### Post by adriandown on 2008-10-09
I've checked with some other Ubuntu users, and they confirm the same behavior.  If there is no known workaround, should I report this as a bug in Ubuntu, or is it a bug in the bash shell?  I use bash on my other computer, running Mac OS X, and I don't see the same behavior, so I assume it is something particular to the way expansions are handled in the version of bash that is standard on Ubuntu?

---

### Post by eweibust on 2008-11-17
@adriandown: I'm having the same problem and it's driving me crazy!  Did you open a bug with Ubuntu?  If not, I will!  Did you find a solution?

Thanks...
Erik

---

