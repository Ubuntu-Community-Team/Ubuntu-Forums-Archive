---
title: "Linking a binary to /bin"
date: 2008-08-28
forum: General Help
---

### Post by Tadhg on 2008-08-28
Right, I'm not great with symbolic linking, so I want to see why this doesn't work.

I downloaded a standalone program. I want to keep the folder (with all its libraries) in, say, /usr/src. But I want to be able to run the binary from command line, so I want to link the programs binary (in /usr/src) to /bin or /usr/local/bin.

I've tried creating a symbolic link from the file to the folder /bin but it doesn't seem to work

Why is this?

---

### Post by aloshbennett on 2008-08-28
> sudo ln -s /usr/src/myprog.sh /bin/myprog.sh
should work.

But i'd suggest you change your classpath to include the /usr/src too, intead of linking your program to /bin

Add this to your ~/.bashrc
> export PATH=/usr/src/:$PATH;

---

