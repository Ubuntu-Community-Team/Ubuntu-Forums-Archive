---
title: "open office 3 installation"
date: 2008-10-01
forum: General Help
---

### Post by jimrie on 2008-10-01
Hi everyone,
i am using 8.04 ubuntu and wish to install open office 3 rc2 but cant figure out how to can you give me simple instructions on how to please, i have already extracted the 64bit tar file and it is called OOO300_m8_native_packed-1_en-US.9357
thought it might help if your going to be giving me terminal commands

cheers guys and gals :D

james

---

### Post by The Cog on 2008-10-01
Inside the extract, you will find a directory with lots of .deb files in it. Open a terminal in that directory and enter the command
> sudo dpkg -i *.deb
which installs the program in /opt. I put a launcher script in a file called /usr/local/bin/ooo with these contents:
> #!/bin/sh
/opt/openoffice.org3/program/soffice "$*"
and I launch it with the command **ooo**.

There is another directory in the extract with debs for "desktop integration" but I haven't installed that because I am worried that it might interfere with the original Ubuntu desktoop entries. I suppose I ought to try it some time though.

---

