---
title: "How to use apt-get to install aptitude..."
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by rnickens on 2009-02-26
I would like to have both apt-get and aptitude working properly on my Ubuntu 8.10 install. However, when I run the command apt- get install aptitude I get the following error: 

```
root@lixx-xxx:~# apt-get install aptitude
Reading package lists... Done
Building dependency tree... Done
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package aptitude has no installation candidate
root@lixx-xxx:~# 
```

(Ubuntu 8.10 minimal install)

Can someone please provide a working example to help me have both tools installed properly?
Thank you.
-rln

---

### Post by sudosu on 2009-02-26
> **rnickens said:**
> I would like to have both apt-get and aptitude working properly on my Ubuntu 8.10 install. However, when I run the command apt- get install aptitude I get the following error: 

```
root@lixx-xxx:~# apt-get install aptitude
Reading package lists... Done
Building dependency tree... Done
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package aptitude has no installation candidate
root@lixx-xxx:~# 
```

(Ubuntu 8.10 minimal install)

Can someone please provide a working example to help me have both tools installed properly?
Thank you.
-rln

have you tried something like:

```
sudo aptitude install <something-you-want-to-install>
```

or you can just run 

```
sudo aptitude
```

to run aptitude.

---

### Post by rnickens on 2009-02-26
Here is a solution that worked for me:

```

# apt-get update
# apt-get upgrade
# apt-get install aptitude
```

---

