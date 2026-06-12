---
title: "Installing KDE 4"
date: 2008-11-17
forum: General Help
---

### Post by solarwind on 2008-11-17
Using the following two guides, I have compiled KDE 4 from source (trunk):

[http://techbase.kde.org/Getting_Started/Build/KDE4/Kubuntu_and_Debian](http://techbase.kde.org/Getting_Started/Build/KDE4/Kubuntu_and_Debian)
[http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4)

I now have a user with a bunch of libraries, executables and compiled objects. Now what? How do I install them?

When I do *sudo make install*, it tells me there is *no rule to make target install*.

However, during the build process, I used ***cmakekde*** rather than [B][I]cmake -DCMAKE_BUILD_TYPE=Release . && make && make install
[/I][/B]. The latter creates a release build whereas the former creates a debug build. I don't want to have to recompile (this could take many hours).

Also, if I have a KDE 4 (kubuntu-desktop) installation, is it safe to install what I just compiled over the ones that were installed from the repositories?

---

### Post by DGortze380 on 2008-11-17
I'm sorry you've already done all this compiling.. all you had to do was:

```

sudo apt-get install kde4

```

---

### Post by solarwind on 2008-11-17
> **DGortze380 said:**
> I'm sorry you've already done all this compiling.. all you had to do was:

```

sudo apt-get install kde4

```

I'm sorry I didn't state this before. I didn't want to install the old KDE 4.1 nonsense. The svn trunk has a lot of improvements that I want. I don't want Ubuntu's old builds. That's why I compiled it myself in the first place.

---

### Post by DGortze380 on 2008-11-17
> **solarwind said:**
> I'm sorry I didn't state this before. I didn't want to install the old KDE 4.1 nonsense. The svn trunk has a lot of improvements that I want. I don't want Ubuntu's old builds. That's why I compiled it myself in the first place.

i.c. well, never installed a desktop from source before, but I would think it's just a typical:

./configure
sudo make
sudo make install

---

### Post by Crafty Kisses on 2008-11-17
You probably have this package, but this package is necessary for compiling:
```
sudo apt-get install build-essential
```

---

### Post by solarwind on 2008-11-17
*face palm*

I have successfully compiled it. However, the Makefile has no *install* target. Therefore, it is not possible to do *make install*. There are, however, a bunch of folders in my build tree that resemble root folders. So how do I install? This is building KDE 4 svn trunk using CMake.

---

### Post by solarwind on 2008-11-17
> **DGortze380 said:**
> i.c. well, never installed a desktop from source before, but I would think it's just a typical:

./configure
sudo make
sudo make install

Unfortunately, the last step will NOT work for me.

---

### Post by solarwind on 2008-11-17
So is there a guide or something to installing KDE 4 svn from source on Ubuntu?

---

