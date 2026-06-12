---
title: "trying to install terminal applet"
date: 2008-09-06
forum: General Help
---

### Post by douggiephresh on 2008-09-06
Im trying to install this applett 


I've created a small little terminal applet. Its my first applet (and my first gtk program). Its really a very simple applet, but hopefuly someone will find it useful.
[Q]



The only dependency is libvte.
[Q]



To install, unpack the tar.gz to a folder and run the following commands.
[Q]



 
cd awn-terminal
./autogen.sh
make
sudo make install
[Q]
 




If you encounter any unmet dependencies in the process, just install them and try again.
Comments and suggestions are appreciated.



when i type cd awn-terminal, i get this

bash: cd: awn-terminal: No such file or directory

I have extracted the files to a folder on my desktop labeled awn-terminal

---

### Post by Anzan on 2008-09-06
Put it in your home dir. Or cd to desktop then the awn-terminal dir.

---

