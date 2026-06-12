---
title: "Problem with xutils-dev on Ubuntu 8.10"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by Oluwajobi on 2009-03-02
I am trying to untar and run a software package on ubuntu 8.10.
I untared it and then gave the command:

<xmkmf> (to be able to make the 'makefile'.)

but it complained that it couldn't see <xutils-dev>.

1st question: How do l get the <xutils-dev> package?


Well, l tried the internet, and got one package (which l don't know whether is the right one - xutils-dev_7.4+3.tar).


2nd question: In which directory should l copy it to recognise
it? Then, how do l copy it there? 
I tried to copy it into the root - but l wasn't allowed.

I used the command $aptitude search xutils
to search for the package, but l couldn't locate it.

What is wrong with my Ubuntu 8.10?

Any help?

Thanks.

Jide

---

### Post by Partyboi2 on 2009-03-05
If you are connected to the internet then open a terminal and install xutils-dev
```
sudo apt-get install xutils-dev
```

If you don't have internet then you can go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=xutils-dev+&searchon=names&suite=intrepid&section=all") and download the deb package and double click to install.

---

### Post by Oluwajobi on 2009-03-08
Thanks.

Jide

---

