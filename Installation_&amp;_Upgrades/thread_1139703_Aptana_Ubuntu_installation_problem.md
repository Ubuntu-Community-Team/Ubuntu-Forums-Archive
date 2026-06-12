---
title: "Aptana Ubuntu installation problem"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by freshT on 2009-04-27
Hi,
I'm trying to install AptanaStudio for linux.
I'm on Ubuntu Intrepid 8.10.
I've read many threads on this and have done the following:
downloaded xulrunner 1.8 to usr/lib/
created the following script: "#!/bin/bash
export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
/usr/local/aptana/AptanaStudio #filepath to Aptana folder"
I've made the script executable.
I've downloaded JRE but was confused by the following:
"setup JRE 1.6 x
"ls -l /usr/local/aptana/jre
/usr/local/aptana/jre -> /usr/java/jrel.6.0""
So maybe i've done something wrong here.

When i double click the file "runAptana.sh" the icon for Aptana displays and the orange progress bar starts with loading workbench plus some other instructions but then it stalls with the following message:
"An error has occurred. See the log file
/home/matt/Aptana Studio/.metadata/.log."

I'm a recent convert to Linux.
Can anybody help me understand what's going on?

Many thanks
Matt

---

