---
title: "[SOLVED] Broken libc6 after using update manager"
date: 2008-09-28
forum: General Help
---

### Post by stinkinrich88 on 2008-09-28
Hello,

I tried to install my recommended updates as usual and now I have a broken libc6 package. When I try to fix it I get the following output:

```
Preconfiguring packages ...
(Reading database ... 238448 files and directories currently installed.)
Preparing to replace libc6 2.7-10ubuntu3 (using .../libc6_2.7-10ubuntu4_amd64.deb) ...

A non-dpkg owned copy of the libc6-i686 package was found.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.7-10ubuntu4_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.7-10ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

That is the output after running sudo apt-get install -f. 

I am running hardy 64bit. 

Thanks!

---

### Post by stinkinrich88 on 2008-09-29
bump

---

### Post by Excalibre on 2008-09-29
> **stinkinrich88 said:**
> Hello,

I tried to install my recommended updates as usual and now I have a broken libc6 package. When I try to fix it I get the following output:

```
Preconfiguring packages ...
(Reading database ... 238448 files and directories currently installed.)
Preparing to replace libc6 2.7-10ubuntu3 (using .../libc6_2.7-10ubuntu4_amd64.deb) ...

A non-dpkg owned copy of the libc6-i686 package was found.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.7-10ubuntu4_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.7-10ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

That is the output after running sudo apt-get install -f. 

I am running hardy 64bit. 

Thanks!
Did you install a version of the libc library some other way than through a package manager at some point?

---

### Post by stinkinrich88 on 2008-09-29
> **Excalibre said:**
> Did you install a version of the libc library some other way than through a package manager at some point?

No, not that I know of. I haven't done any fiddling with ubuntu for months, now.

---

### Post by Excalibre on 2008-09-29
> **stinkinrich88 said:**
> No, not that I know of. I haven't done any fiddling with ubuntu for months, now.
Hmm. Because that's what the error message implies.

There are various options to force installation of packages over dpkg's protestations. I think you can see those options by running "dpkg --help". Then download the package and try a force install. It might break something, though.

---

### Post by stinkinrich88 on 2008-09-30
> **Excalibre said:**
> Hmm. Because that's what the error message implies.

There are various options to force installation of packages over dpkg's protestations. I think you can see those options by running "dpkg --help". Then download the package and try a force install. It might break something, though.

is there a way I can use the live cd to repair my libc6?

---

### Post by stinkinrich88 on 2008-09-30
solved! I used my own advice from here: [http://ubuntuforums.org/showthread.php?t=724359]("http://ubuntuforums.org/showthread.php?t=724359")

turns out I had the exact same problem before! 

Thanks for helping, Excalibre!

---

### Post by nmsmith on 2009-05-01
The link you provided ([http://ubuntuforums.org/showthread.php?t=724359](http://ubuntuforums.org/showthread.php?t=724359)) appears broken. Can you illuminate what you did? I have the same problem as you now (caused due to accidentally enabling an intrepid repository in hardy).

---

### Post by nmsmith on 2009-05-01
Nevermind - I found a solution here: [http://www.debianhelp.org/node/12820](http://www.debianhelp.org/node/12820)

The solution was to remove (or at least rename) /lib/i686/cmov/libc.so.6

---

