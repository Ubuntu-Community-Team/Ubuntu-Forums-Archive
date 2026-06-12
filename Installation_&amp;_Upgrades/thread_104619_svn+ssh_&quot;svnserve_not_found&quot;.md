---
title: "svn+ssh &quot;svnserve not found&quot;"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by traelon on 2005-12-16
Hello.

I try to checkout from a repository  svn+ssh://[..] using svn.

After entering password I get the error message

"svnserve: Command not found."

Google didnt return anything that would help me though many users seem to have that problem. None of the suggestions helped for me.

/usr/bin as well as /usr/bin/X11 are part of $PATH.

I have no clue what so ever could be the reason for that.
I can connect to the server where the repo is at using ssh.

Thanks for your help

Holger

---

### Post by Leif on 2005-12-16
sorry if this is a dumb question, but do you have subversion installed ?

---

### Post by traelon on 2005-12-17
Yes, subversion 1.2.0-1ubuntu1 is installed.

svn and svnserve are both available.

---

### Post by traelon on 2005-12-21
The PATH variable on the server wasn't correct!!

---

