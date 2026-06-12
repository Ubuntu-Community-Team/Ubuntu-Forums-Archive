---
title: "Private Ubuntu mirror"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by maddis on 2009-01-19
I need to be able to access Ubuntu mirror without internet connection. For that I tried to download the current ubuntu mirror, but after searching the ubuntu documents and seeing what was being downloaded I realize there is too much to download and most of the stuff is something I don't need.

I only need i386 version and preferable only one distribution(hardy), not all.

Is there any tool for that or do I just have to manually first get the file list, then grep all except i386 related stuff out there and then feed that list to for example wget or rsync?

There was instruction how to become mirror, but that is not what I'm trying to do here.

---

### Post by Partyboi2 on 2009-01-19
Have you looked at [[COLOR=Blue]aptoncd[/COLOR]]("http://aptoncd.sourceforge.net/")?

---

### Post by maddis on 2009-01-19
That seems good program, but I'm not sure if it's just the right one for me. 

It seems that it only saves those packages that are already installed in to system. So in order so save them all I would first have to install them all to one system. Of course that could be done, but it might take quite a long time to do that.

Thought it still might be easier than starting to grep correct packages from filelist from actual ubuntu mirror.

---

### Post by Partyboi2 on 2009-01-19
Another option if you have high bandwidth maybe could be to download the hardy repos dvd and use that.
See
[[COLOR=Blue]Orginal[/COLOR]]("http://wiki.ubuntu-id.org/DistribusiDvdReposUbuntu") or the
[[COLOR=Blue]Translated Version[/COLOR]]("http://translate.google.com/translate?prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwiki.ubuntu-id.org%2FDistribusiDvdReposUbuntu&sl=auto&tl=en&history_state0=")

---

### Post by maddis on 2009-01-19
That seems a little better since I had hard time installing everything to the system.

One thing though. It's quite obvious that those dvd-repositories are not maintained by Ubuntu so I'm bit worried what might happen them in the future.

But for now it seems best (or at least easiest) way to go. Thanks.

---

### Post by tribaal on 2009-01-19
The solution I'm using is to use the "apt-mirror" package... this lets me mirror specific repositories and serve them to my business's internal machines.

This is the software that runs on "official" mirrors.

You can also have a look at apt-cache, in case you don't want to download the whole repository.

Hope this helps

- Trib'

---

### Post by maddis on 2009-01-20
Apt-mirror looks pretty much exactly what I was looking for! Thanks. I'll give it a try.

---

