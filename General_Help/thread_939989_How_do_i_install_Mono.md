---
title: "How do i install Mono?"
date: 2008-10-06
forum: General Help
---

### Post by xmrkite on 2008-10-06
Hello, sudo apt-get install mono doesn't work. 

Anyone know how to install mono?

-Thanks

---

### Post by Titan8990 on 2008-10-06
What error do you get from sudo apt-get install mono?

---

### Post by xmrkite on 2008-10-06
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate

---

### Post by kramulous on 2008-10-07
When I "sudo aptitude search mono" I get everything including:

mono-runtime, mono-jit, mono-common, etc.

Can you "sudo aptitude install mono-runtime mono-jit mono-common" ?

---

### Post by Sef on 2008-10-07
> When I "sudo aptitude search mono" I get everything including:

mono-runtime, mono-jit, mono-common, etc.

Can you "sudo aptitude install mono-runtime mono-jit mono-common" ?

You could also do ```
sudo apt-get install mono-runtime mono-jit mono-common
```.

---

### Post by xmrkite on 2008-10-07
Ok, that worked nicely. Thanks for the help.

---

