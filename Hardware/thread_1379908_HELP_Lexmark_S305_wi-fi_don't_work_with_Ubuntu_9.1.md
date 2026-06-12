---
title: "HELP: Lexmark S305 wi-fi don't work with Ubuntu 9.10 -AMD Athlon 64"
date: 2010-01-13
forum: Hardware
---

### Post by brizio on 2010-01-13
Help me!
I bought the Lexmark S305 and I downloaded the following driver lexmark-inkjet-09-driver-1.0-1.i386.deb.sh "because Ubuntu did not recognize.

 After the first stages of the installation you receive the following error message: "Execute: dpkg-i-Lexmark Inkjet-09-driver-1.0-1.i386.deb 2> & 1 | tee / home / nicola / lua_ixdeyG / installerror_msgs

dpkg: error in lexmark-inkjet-09-driver-1.0-1.i386.deb (- install):
 the architecture of the package (i386) does not match that of the system (amd64)
There were errors in:
 lexmark-inkjet-09-driver-1.0-1.i386.deb. "

and the installation stops.
The S.O. bit Ubuntu 9.10 and the processor is an AMD Athlon 64.
I wonder if the procedure is also indicated in my case.
Thank you very much.

---

### Post by .nedberg on 2010-01-13
You have downloaded a 32bit driver, you'll need the 64bit version to match you os-architecture.

---

### Post by brizio on 2010-01-13
Where can I find them?

---

### Post by .nedberg on 2010-01-13
You should find them at the same page where you found the 32bit drivers. If they exist...

---

### Post by trickstyhobbit on 2010-07-19
This worked for me although I haven't tried using the wifi capabilities yet. It at least gives you some functions.
[http://ubuntuforums.org/showthread.php?t=855415](http://ubuntuforums.org/showthread.php?t=855415)

---

