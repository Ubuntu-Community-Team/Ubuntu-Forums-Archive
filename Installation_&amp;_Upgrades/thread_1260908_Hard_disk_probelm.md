---
title: "Hard disk probelm"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by urgood2 on 2009-09-08
Is there any way to install Ubuntu on disk drive D?

I think my local disk drive is C::confused:

---

### Post by raymondh on 2009-09-08
> **urgood2 said:**
> Is there any way to install Ubuntu on disk drive D?

I think my local disk drive is C::confused:

You can install Ubuntu "inside windows" and select "disk drive D".  That is known as a WUBI install.  Do read the pros and cons of a wubi-install.  The advantage is the convenience in installing/uninstalling.  A major disadvantage is that a wubi-installed Ubuntu is dependent on a healthy windows (i.e. if windows crashes, so does Ubuntu, etc).

Another install method is to put Ubuntu in it's own partition ... choosing which OS to boot into when you start your computer.  In this method, linux does not differentiate as drive C, D, or E.  Rather, it will show either sda1, sda2, hd0, hd1, etc. (depending on where you install).

Either way, back-up your files and defrag windows (2x or more if you have the time).  Some reading/reference materials for you:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Good luck.  Post back if you need further assistance.  Happy ubuntu-ing.

---

