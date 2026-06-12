---
title: "Opening/installing Postal 2 demo from tar.bz2"
date: 2008-08-28
forum: General Help
---

### Post by carl99fan on 2008-08-28
I have downloaded a few games and started learning how to navigate the terminal change directories and I make install.
someone once told me that if it is a tar.bz2 then I just click the run file and I'm on my way.
this worked for postal multi player but I can't figure this demo out.
I click run and nothing.
A little instruction usually takes me a long way! 
I thank you in advance.

---

### Post by aloshbennett on 2008-08-29
cd to the directory containing the tar.bz2 and try
> tar -xvvf --bzip2 game.tar.bz2

tar is the command that creates and extracts tar files.
  -x extracts
  -vv very very verbose :)
  -f  from file
  --bzip2 use bzip2 format for the action

For the sake of the example I am calling your file game.tar.bz2

---

### Post by tuxxy on 2008-08-29
You need to compile it from source

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

