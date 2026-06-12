---
title: "installing Winrar"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by roaddummy on 2008-12-11
I had this program called Winrar on Vista before I got Ubuntu.  It is a program that allows you to unzip any kind of zipped file.  I do a lot of digi scrapping so I am constantly getting files with the .rar extension on them.  I have a version of Winrar that is for Linux.  Problem is that I do not know how to or where to put it in my program files or where to put it to install it.  I really would like to get this installed so I can download some stuff that I need.  The only other option I would have is to take it to work and I don't want to do that.  It is too much of a hassle to unzip it there.  Please remember that I am new to Linux and that I need good instructions that are simple to follow!!!  I am still learning and the easier the better right now.  Maybe one day I will computer literate!!!!:lolflag:

Melanie
[http://88designs.blogspot.com](http://88designs.blogspot.com)

---

### Post by taurus on 2008-12-11
What is the complete name of the rar file that you downloaded?  Bet you need to unpack it first before you can use it.  However, there is already one from the repos so just open a terminal and install it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install unrar
unrar
```

---

### Post by Mark Phelps on 2008-12-11
Linux is a completely different structure than Windows.  There is no Program Files directory.  In order to "install" WinRAR, which is a Windows program, you would have to install Wine -- which is a lot of work in and of itself, not so much the installation, but getting anything to work.

There are Linux archive handling packages that do much the same stuff as WinRAR -- as pointed out in the post above.  Recommend you use them instead of taking on Wine and all it's associated problems.

---

