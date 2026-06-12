---
title: "Nethack install"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Saiyan Fury on 2009-03-15
Alright, here goes.

I am trying to install Nethack on Ubuntu 8.04.  I do the usual
"sudo apt-get install nethack" and I get this message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nethack is a virtual package provided by:
  nethack-x11 3.4.3-10.5ubuntu1
  nethack-qt 3.4.3-10.5ubuntu1
  nethack-lisp 3.4.3-10.5ubuntu1
  nethack-console 3.4.3-10.5ubuntu1
You should explicitly select one to install.
E: Package nethack has no installation candidate

```

Therefore, I go ahead and pick the first one, and I receive this error message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3.4.3-10.5ubuntu1

```

I've searched the forums, and have gleaned nothing.  Any and all help will be appreciated.

---

### Post by Saiyan Fury on 2009-03-15
So I just double-checked my files, and I have the /usr/games/lib/nethackdir/ installed, but idk what to with it.

---

### Post by unutbu on 2009-03-15
Have you tried
```

sudo apt-get install nethack-x11
```
?

---

### Post by Saiyan Fury on 2009-03-15
I just tried it, and got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nethack-xll

```

---

### Post by unutbu on 2009-03-15
x11 has two one's in it, not two lowercase L's. Try that.

---

### Post by Saiyan Fury on 2009-03-15
Oh wow, I feel stupid.

Anyway, it appears to have worked.  Many thanks, my friend.

---

