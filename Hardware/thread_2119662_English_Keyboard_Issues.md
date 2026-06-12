---
title: "English Keyboard Issues"
date: 2013-02-24
forum: Hardware
---

### Post by Juan Christian on 2013-02-24
Hello, I have a Sager NP9370 laptop with numeric key pad and since I installed Ubuntu 12.10 through VirtualBox I cant write correctly, see below:

> Using _USA Alternative International (former us_intl)_, I get these problems:

Instead of ç I receive &#263;, when I press ´ + c

Instead of ""/''  I receive ¨¨/´´

> Using _USA_, I get these problems:

Instead of á/é/í/ó/ú/ç I receive 'a/'e/'i/'o/'u/'c

But now ""/'' is OK

--------------------

Help me please, I'm a programmer, so is fundamental a correct keyboard layout.
Thanks in advance.

---

### Post by cipricus on 2013-04-15
My solution in  Xfce Quantal to a more limited bug reported [here]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/518056") was to install the `ibus` package and its dependencies.  ([source]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/518056/comments/15"))  

Try and see if this helps.

---

