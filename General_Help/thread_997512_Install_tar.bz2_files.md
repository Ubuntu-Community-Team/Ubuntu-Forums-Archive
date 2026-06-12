---
title: "Install tar.bz2 files"
date: 2008-11-29
forum: General Help
---

### Post by Captain_Falafel on 2008-11-29
I've got Amarok's first candidate release, Narwhal, unpacked in a directory.
And now, I've got no clue what to do. :confused:

---

### Post by Washer on 2008-11-29
When you have source code, extract it & run *make* then if that works do *make install*. Later *make uninstall *to remove.

It's kind of a bitch compiling cuz of all the dependencies you have to manually take care of. I'd look around for a .deb first, there's probably one out there.

---

### Post by Washer on 2008-11-29
Sacrificing virgins also helps & no, not the basement dwelling nerd type.

---

### Post by Captain_Falafel on 2008-11-30
> **Washer said:**
> When you have source code, extract it & run *make* then if that works do *make install*. Later *make uninstall *to remove.

It's kind of a bitch compiling cuz of all the dependencies you have to manually take care of. I'd look around for a .deb first, there's probably one out there.

I'll have to admit.. this has been a bitch lol. I've looked around, but there's no .deb file.. I believe it's fairly new since it's a candidate release.
However, when I run make, it doesn't work and says 'could not find make file' so I looked in the directory and found a cmake file. So I installed cmake, and ran it, and it still wouldn't do anything. :confused:
Worst case scenario, I'll wait until they have a final release

---

### Post by Washer on 2008-11-30
Or you could just read the README & the INSTALL files, there's always that

---

### Post by taurus on 2008-11-30
Usually but not always, you would do these steps.

```
./configure
make
sudo make install
```
./configure will check your system for all the necessary libraries so if you are missing something, it will tell you.  Then, you can go into synaptic and install the package plus the developing (-dev) too.

---

### Post by Captain_Falafel on 2008-11-30
> **Washer said:**
> Or you could just read the README & the INSTALL files, there's always that

I think it's a lost cause. I read the readme and install files and tried installing the required dependencies with no luck. I'm just gonna wait for the official version Amarok 2 to come out.

Thanks for the replies though. At least I learned how to go around working with tar.bz2 files and compilation. I ended up compiling a different program with ./configure, make, sudo make install.. and it worked :popcorn:

---

### Post by MickS on 2008-11-30
> **Captain_Falafel said:**
> I think it's a lost cause. I read the readme and install files and tried installing the required dependencies with no luck. I'm just gonna wait for the official version Amarok 2 to come out.

Thanks for the replies though. At least I learned how to go around working with tar.bz2 files and compilation. I ended up compiling a different program with ./configure, make, sudo make install.. and it worked :popcorn:

You can get Amarok 2 here [http://www.kubuntu.org/amarok2-beta2](http://www.kubuntu.org/amarok2-beta2)

To be honest I think I prefered the old one.

Mick

---

### Post by Captain_Falafel on 2008-11-30
> **MickS said:**
> You can get Amarok 2 here [http://www.kubuntu.org/amarok2-beta2](http://www.kubuntu.org/amarok2-beta2)

To be honest I think I prefered the old one.

Mick

yeah.. I love Amarok 1, and I had the Amarok-nightly builds and sources in, and played around with the alphas, which weren't too good. But I was hoping that the release candidate was much better.

---

### Post by soro2005 on 2008-11-30
[Look here](http://www.kubuntu.org/news/amarok-2-rc-1). If you want to install something bleeding edge, you can often find it in the Personal Package Archive (PPA) of somebody, often even the official Ubuntu packagers.

---

