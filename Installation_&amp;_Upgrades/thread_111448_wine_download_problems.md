---
title: "wine download problems"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by bdd4 on 2006-01-02
I'm unable to install switchercadiii.exe with wine. results were:

bp@bphostname:~$ cd winapps
bp@bphostname:~/winapps$ ls -l
total 5596           
-rwxrwxrwx  1 bp bp 5718016 2005-12-22 09:40 swcadiii.exe (my note: is a binary file)
bp@bphostname:~/winapps$ wine switchercadiii.exe
wine: cannot find 'switchercadiii.exe'

so i relaoded wine sudo apt-get update and the results was:

Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
bp@bphostname:~/winapps$
i suspect that since i can't download some wine (bnary) files that is the reason i can't wine binary file switchercadiii.exe.

what can i do to get the binary wine files ?

thx

bdd4

---

### Post by ape on 2006-01-02
From the directory listing you've given, the binary file name is swcadiii.exe, not switchercadiii.exe.  Is there any chance you're just typing the wrong filename?

---

### Post by bdd4 on 2006-01-02
THANK YOU !!!!!

minor error on my part - MAJOR  results you were right.

THANK YOU

bdd4

---

### Post by dcstar on 2006-01-03
[QUOTE=bdd4]
.......
so i relaoded wine sudo apt-get update and the results was:

Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
.......
what can i do to get the binary wine files ?
.......[/QUOTE]
And to follow up, the servers where those wine binaries exist are horribly unreliable straight after they release a new version, it has taken me 4-5 restarts to finally download all of the updates the last few times (like the other day). This is the problem you have also experienced.

I've now "pinned" my wine version so I don't get annoyed by this problem again.

---

