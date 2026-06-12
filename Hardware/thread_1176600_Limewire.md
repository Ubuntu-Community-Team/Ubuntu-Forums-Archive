---
title: "Limewire"
date: 2009-06-02
forum: Hardware
---

### Post by aaron2073 on 2009-06-02
My children have Limewire on their laptops, with only 6.8 gb of memory on these little computers, Is that potentially bad..
Right now one of the computers has 6.5 of 6.8 gb used... How do I clean up some not needed materil.

---

### Post by MichaelSammels on 2009-06-02
Open Synaptic Manager, and uninstall packages you don't need. Possibly purchase an Extra Hard Drive, or remove some of the downloads.

---

### Post by aaron2073 on 2009-06-02
New to the lingo.. "Packages" are programs..?
THank you for the help, this maybe be causing the issues I am having with the upgrades. Unmet discrepencies.....I posted about this under search Restore Points.
Not knowing about this makes everything tough.. but learning on the fly..

---

### Post by Therion on 2009-06-02
> **aaron2073 said:**
> New to the lingo.. "Packages" are programs..?
Mmmm... Close.  Packages are more like building blocks that, when assembled, make a "program".  
Programs are more typically referred to as "applications" these days.

> **aaron2073 said:**
> ...Unmet discrepencies...
More lingo for you to digest: Unmet *dependencies*. 
Those happen because some packages rely (they're dependent!) on other packages to build a specific application.  

To free up some space you could go to Add/Remove and see if there are some *applications* you could remove from your system.  Besides that, the best thing would probably be to migrate the music files somewhere else.

---

### Post by cariboo on 2009-06-02
There are also archived packages in /var/cache/apt/archives, you don't need to keep them and depending on how many extra programs have been installed they might be taking up a fair amount of hard drive space. to clean thes out open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and just in case, in the same terminal:

```
sudo apt-get autoremove
```

---

