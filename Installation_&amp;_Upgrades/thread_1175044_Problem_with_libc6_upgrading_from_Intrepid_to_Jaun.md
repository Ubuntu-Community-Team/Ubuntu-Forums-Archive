---
title: "Problem with libc6 upgrading from Intrepid to Jaunty"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by warhammerkid on 2009-05-31
I ran the dist-upgrade, it updated all of my sources, and then it crashed. Now, if I run apt-get upgrade, I get the following:
```

me@neuromancer-64:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  binutils: Depends: libc6 (>= 2.8) but 2.8~20080505-0ubuntu9 is installed
  cpp-4.3: Depends: libc6 (>= 2.8) but 2.8~20080505-0ubuntu9 is installed
  g++-4.3: Depends: libc6 (>= 2.8) but 2.8~20080505-0ubuntu9 is installed
  libc6-dev: Depends: libc6 (= 2.9-4ubuntu6) but 2.8~20080505-0ubuntu9 is installed
  libc6-i386: Depends: libc6 (= 2.9-4ubuntu6) but 2.8~20080505-0ubuntu9 is installed
  libxext-dev: Depends: libxext6 (= 2:1.0.99.1-0ubuntu3) but 2:1.0.4-1 is installed
E: Unmet dependencies. Try using -f

```

Running apt-get install -f gives me:
```

me@neuromancer-64:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libxext6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libxext6
2 upgraded, 0 newly installed, 0 to remove and 1262 not upgraded.
47 not fully installed or removed.
Need to get 0B/4985kB of archives.
After this operation, 348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on libc6

```

I managed to find some other info around the net searching for "Could not perform immediate configuration...", but none of it solves the problem so I'm kind of at a loss. Some people say that it's due to a bad version of libc6, but I upgraded to Intrepid without any problems, so I'm not really sure what's going on.

---

### Post by kruegger on 2009-05-31
me@neuromancer-64:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libxext6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libxext6

[SIZE="4"]2 upgraded, 0 newly installed, 0 to remove and [COLOR="Red"]1262 not upgraded.[/COLOR][/SIZE]

47 not fully installed or removed.
Need to get 0B/4985kB of archives.
After this operation, 348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on libc6


The enlarged piece of code says 2 packages have been upgraded 1262 packages haven't been upgraded, I guess that the upgrade to Jaunty was failed.
What you've got now are libc6 and libext6 in Jaunty and the rest of it in Intrepid. Hence, the internal error.

Get rid of those two packages and perform an actual upgrade with Updater Manager. I'd do it.

Nothing to lose.

---

### Post by warhammerkid on 2009-05-31
Actually, it says that to fix the dependency problem, it's going to try to upgrade 2 packages. I don't know exactly what happened, but libxext and libc6 are both on their older version (as evidenced by the dependency description which describes newer versions for both of them).

---

### Post by kruegger on 2009-06-01
> **warhammerkid said:**
> Actually, it says that to fix the dependency problem, it's going to try to upgrade 2 packages. I don't know exactly what happened, but libxext and libc6 are both on their older version (as evidenced by the dependency description which describes newer versions for both of them).

You are right, ha,ha,ha. I saw the bottle half empty.
Still, how bizarre.:-k

---

