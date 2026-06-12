---
title: "Is there a &quot;World&quot; file in ubuntu ..."
date: 2007-04-30
forum: Gentoo and derivatives
---

### Post by garlik42 on 2007-04-30
I find myself often rebuilding a system for different reasons (usually because I screwed something up ...) and on my gentoo boxes, if I want to take a "snapshot" of how the system was set up, I make a copy of /etc and a copy of the world file. /etc to give me how stuff is configured, and world so I know what I have installed.

My question, is: Is there a file somewhere on my ubuntu system, that has all the packages I have requested to be installed (not nesessarily dependancies) ? So if I want to take a systems configuration and copy it, it will be a bit easier.

Thanks.

---

### Post by jfinkels on 2007-04-30
[http://kmandla.wordpress.com/2007/04/25/stash-your-cache/](http://kmandla.wordpress.com/2007/04/25/stash-your-cache/)

Of course, if you empty your cache sometime, these .deb files won't be there...

---

### Post by garlik42 on 2007-04-30
Thanks, I was aware of the cache, but I was looking for a listing of packages that were installed, that would not nesessarily depend on the cache, some of the systems I have don't have the space to keep all those package files, so I typically clean them out occasionally.

---

### Post by jfinkels on 2007-04-30
> **garlik42 said:**
> Thanks, I was aware of the cache, but I was looking for a listing of packages that were installed, that would not nesessarily depend on the cache, some of the systems I have don't have the space to keep all those package files, so I typically clean them out occasionally.

Yeah, I realized that after I posted. You could do this command:
```
sudo dpkg -l | cut -d " " -f 3

```
which lists all applications installed and "cut"s out just the names of each package. You can then insert that into a file I suppose...for example, a file named "installedpackages"...
```

sudo dpkg -l | cut -d " " -f 3 > installedpackages

```

---

### Post by garlik42 on 2007-04-30
That's the ticket!!

Thanks, looks like I need to become friends with this dpkg program, I guess it's similar to the gentoo-toolkit programs like qpkg qfile etc.

Thanks again.

---

### Post by funkyFlash on 2009-01-19
It'd be nifty if I could take this a step further.  Do you know where dpkg keeps this information?  The manpage doesn't have a "files" section, so that rules that out.

Here's what I'm getting at: with gentoo, I can copy my world file from my old system to a fresh system, type something along the lines of "emerge world", then it will happily calculate deps, and emerge it's heart out until it has all of the packages that were installed on my old system.  I'm looking for a similar solution, where I could just copy apt's record of installed packages from one system to another, do an "apt-get upgrade" or something, and it would pound away until all packages are installed.

---

