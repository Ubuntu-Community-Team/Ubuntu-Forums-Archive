---
title: "[SOLVED] My compiles crash because of gcc-3.3-doc and gcc-3.4-doc"
date: 2008-07-29
forum: General Help
---

### Post by harryliddic on 2008-07-29
I can seem to compile anything that requires gcc docs, particularly dpkg.

---

### Post by braddcadd on 2008-07-29
Can you post the error message?

---

### Post by steveneddy on 2008-07-29
please in terminal type

```
sudo apt-get install gcc-4.2 gcc-4.2-base
```

That should do the trick.

---

### Post by harryliddic on 2008-07-29
harry@harry-desktop:~/Desktop/kino-1.3.0$ sudo apt-get install gcc-4.2 gcc-4.2-base
[sudo] password for harry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-4.2 is already the newest version.
gcc-4.2-base is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libfaad2-0 libgfortran2 libaccess-bridge-java
  libkgantt0-dev libksieve0-dev libx264-54 cmake ifeffit libntfs9
  libungif4-dev libktnef1-dev libkpimexchange1-dev libkdepim1-dev libkcal2-dev
  libg2c0 libmimelib1-dev pgplot5 libnetcdf3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gcc-3.3-doc (1:3.3.6-15ubuntu4) ...
sh: cannot open /usr/share/info/gcc-3.3.info.gz: No such file
install-info(/usr/share/info/gcc-3.3.info.gz): 
dpkg: error processing gcc-3.3-doc (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gcc-3.4-doc (3.4.6-6ubuntu3) ...
sh: cannot open /usr/share/info/gcc-3.4.info.gz: No such file
install-info(/usr/share/info/gcc-3.4.info.gz): 
dpkg: error processing gcc-3.4-doc (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gcc-3.3-doc
 gcc-3.4-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

It still is happening.

---

### Post by braddcadd on 2008-07-29
This looks like a version problem.  It looks like you have gcc-4.2 installed ok but some app is looking for gcc-3.4.  I don't think there will be any problems if you have 3.4 & 4.2 installed.  Installing gcc-3.4 (docs, base, etc.) would probably make that error message go away.

---

### Post by harryliddic on 2008-07-29
I have them installed via Synaptic. The problem it seems to me is in 'dpkg' I am going to use an early version of 'dpkg' and see what the results are. If you have any ideas I would sure appreciate them.

---

### Post by braddcadd on 2008-07-30
I guessing here but try:
```

dpkg --force-depends-version -i your_deb_file.deb

```

---

