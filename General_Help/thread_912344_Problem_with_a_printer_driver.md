---
title: "Problem with a printer driver"
date: 2008-09-06
forum: General Help
---

### Post by coldfire204 on 2008-09-06
Hopefully I'm just overlooking something really simple here, but I can't get Ubuntu 8.04 to install this printer driver for me.  I got the tar file off of Lexmark's website and opened that up in my terminal no problem.  The readme file for the driver says that the driver should be ran with the following command:

sh z600cups-1.0-1.tar.gz.sh

When I do that (I tried it with sudo too, still didn't work) the terminal says:

sh: Can't open z600cups-1.0-1.tar.gz.sh

I've looked around for an answer on google and the forums here and I've seen similar threads but they all assume that the sh command works with no problems.  I figure since I can't do it as sudo either, then it's not an access privelege problem.  The file is currently in my Desktop directory, should it maybe be somewhere else?

---

### Post by coldfire204 on 2008-09-06
Looked up info on how to use sh command in linux and got the file open but it says there are checksum errors with the file, at least I got the command to work though I guess:mad:

---

### Post by Shazaam on 2008-09-06
You need to extract (decompress) the tar. Either double-click it, right-click it, or unpack with the terminal. Once you do that you can pass the sudo sh command after you cd (change directory) to the extracted folder/directory.

---

