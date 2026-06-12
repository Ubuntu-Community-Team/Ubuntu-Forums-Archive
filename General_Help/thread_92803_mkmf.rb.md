---
title: "mkmf.rb"
date: 2005-11-20
forum: General Help
---

### Post by ajitomatix on 2005-11-20
Hi,

This is my first post on the Ubuntu forums. I have been using Ubuntu from hoary and I am currently on breezy. I would like to thank the Ubuntu people for putting together a great distro!

Anyways I wanted to install FuseFS which is a ruby interface to the fuse api. The installation halts because it cannot find module mkmf (mkmf.rb). On the FuseFS forum, I was told that it is a part of the standard ruby library, but Ubuntu ruby packages don't seem to include mkmf.rb

I have looked at other ruby packages, they don't seem to have mkmf either. Any suggestions/help on where and how I can find it?

On a related note, is there a way to convert installations like FuseFS to a .deb package?

Thanks in advance!
Ajit

---

### Post by pjstadig on 2006-02-16
I've posted the solution to this problem on [another thread]("http://ubuntuforums.org/showthread.php?p=740643#post740643"). Basically, you need to install the ruby1.8-dev package (or whatever version of ruby you are using). That will give you the 'mkmf' module.

Paul

---

