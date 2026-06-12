---
title: "Adept/Sypnaptic problem"
date: 2008-10-20
forum: General Help
---

### Post by Moonfrost on 2008-10-20
I was trying to update KDE 4.0.3 to 4.1.2 using this repo

```
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
```

Once I added the repo on Adept every time I try to open it, it tells me the following:

```
The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
```

And then it closes, then when I try to open Sypnaptic it tells me something similar:

```
E: Type 'http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

What happened? I got the wrong repo or what? I got it from:

```
https://launchpad.net/~kubuntu-members-kde4/+archive
```

EDIT: Also, I tried what Adept told me, I first tried sudo apt-get update and this came out:

```
moonfrost@moonfrost-desktop:~$ sudo apt-get update
E: Type 'http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu' is not known on line 59 in source list /etc/apt/sources.list
```

Today I tried apt-setup and it showed something, but I didn't copy it so now I tried doing it again and it just says "command not found"...so I don't know.

EDIT #2: Okay, I fixed my problem by watching the last post of this thread:

[http://ubuntuforums.org/showthread.php?t=365154](http://ubuntuforums.org/showthread.php?t=365154)

---

