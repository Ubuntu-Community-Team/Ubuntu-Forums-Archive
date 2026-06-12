---
title: "How do you install .tar.gz?"
date: 2008-08-08
forum: General Help
---

### Post by jras20 on 2008-08-08
What is the command line for .tar.gz files?

Thanks

---

### Post by igotnoluck on 2008-08-08
tar -xvfz file.tar.gz

here is a nice site for linux commands:
[http://www.cplug.org/guides/post-install.html]("http://www.cplug.org/guides/post-install.html")

---

### Post by dannyboy79 on 2008-08-08
this will merely extract the tar ball gzipped to whatever your current directory is. SO I would suggest first making a folder somewhere, move the tar ball file to there, cd to that directory, then run that command. (reasoning behind this: some tarballs contain folders where this isn't neccessary but some just have the flat files without a folder so you can really bugger up a folder.) Then within the folder, there should be some info about how to install it. may be a script, or you may have to follow this guide:
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
You may need to do this first:

```
sudo apt-get install gcc build-essential
```

in order to compile from source.

---

### Post by tuxxy on 2008-08-08
Read the compiling how to

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

