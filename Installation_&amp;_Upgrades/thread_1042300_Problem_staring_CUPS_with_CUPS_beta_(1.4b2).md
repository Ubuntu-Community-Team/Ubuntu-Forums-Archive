---
title: "Problem staring CUPS with CUPS beta (1.4b2)"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by akelsall on 2009-01-17
Has anyone tried compiling and running the new CUPS beta? Everything "seems" to have gone OK (the ./configure, make, and make install), but when I try to restart cups, I get the following message:

> /usr/sbin/cupsd: error while loading shared libraries: libcupsmime.so.1: cannot open shared object file: No such file or directory
cups: unable to start scheduler.
cups: scheduler is not running.


One question I do have is does it matter from which directory I compile and install CUPS? I just made a directory off of my $HOME dir to unpack, compile, and install the beta. 

After the install, I did reboot just for good measure.

Thanks,

Andy

---

### Post by akelsall on 2009-01-19
Found that by copying the file libcupsmime.so.1 from /usr/lib64/ to /usr/lib/, that fixed the problem. Not sure why it got installed in /usr/lib64/ since I'm not running the 64-bit version of Ubuntu.

Andy

---

