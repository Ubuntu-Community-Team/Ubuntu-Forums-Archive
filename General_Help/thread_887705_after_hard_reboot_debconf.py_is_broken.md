---
title: "after hard reboot debconf.py is broken"
date: 2008-08-12
forum: General Help
---

### Post by ds[de] on 2008-08-12
Hi,

after I accidentally put my notebook in suspend mode, I had to forcefully shut it down with the on/off switch because the screen stayed black (I've heard other people complain about this aswell).

Now when I type a command that isn't available in bash (e.g. gibberish) I get a 'Segmentation fault'.
After reading /etc/bash.bashrc and editing out the lines about the 'command-not-found' package, I've found that this problem is linked to my 
/usr/lib/python2.5/site-packages/problem_report.py 
being broken (the file contains binary instead of text).

Now I'm unsure whether it's safe to sudo apt-get remove python python2.5 && sudo apt-get install python python2.5 because a lot depends on those packages as far as I know.

/usr/lib/python2.5/site-packages/problem_report.py probably isn't the only file that's broken, so manually replacing them with a valid file would be a tedious (and maybe unsuccessful) task.

PS: I read somewhere that /usr/lib/python2.5/site-packages/problem_report.py belongs to the package 'python-apport', but re-installing didn't help here.
I use Ubuntu 8.04 btw.

Any suggestions?

Regards,
ds[de]

---

### Post by ds[de] on 2008-08-13
.bump

---

### Post by ds[de] on 2008-08-15
.bump (last one before I'll break my OS by sudo apt-get remove python :)

---

