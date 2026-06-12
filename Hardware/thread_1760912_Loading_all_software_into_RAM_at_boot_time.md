---
title: "Loading all software into RAM at boot time"
date: 2011-05-17
forum: Hardware
---

### Post by aphatak on 2011-05-17
Ubuntu does not appear to need large storage;  I notice that of the 26GB I allocated to the root (which contains everything else), about 17% is in use.  This gives a total of 4420 MB - and this includes all the executables, configuration files, data and so on.  (I have plenty more data, but all of it resides on file servers; this is mounted as nfs volumes once the OS loads.)

My desktop has 16GB of RAM.  I haven't yet seen the swap-space being used, even when I work on large files (such as 160-megapixel photographic images).  So in theory, the entire hard disk contents could be loaded into RAM;  this would still leave close to 12GB free for working storage and cache.

Couple of questions -
[LIST=1]
[*]Will Ubuntu look at the available memory and automatically load all of itself, including all the installed packages, into RAM when space is available?
[*]If it will not, is there a way I can ask the OS to do it, leave the hard-drive alone after that, and then update the hard-disk (a) all in one go when I shut the machine down, re-start or (b) in pieces when the machine is idle?
[/LIST]

---

### Post by amauk on 2011-05-17
Be aware that the disk space needed to store a program / library has no bearing on the amount of RAM that it uses when executed

Think of executable code like a fold-up map
You need little space to actually store the map, but it's not usable
To use, you have to open it up, where it takes up much more space

to use a simple example
```
int main()
{
    int *foo = new int[1000000];
    delete[] foo;
    return 0;
}
```

When compiled, this C++ program takes up very little space on disk (only a few kilobytes)
but the program, when executed, uses a million integers, which takes up approx 4 megabytes of RAM

---

### Post by aphatak on 2011-05-17
Agreed.  However, loading the executable into RAM would still need only tiny amounts of RAM.  If all my software occupies 4GB on the hard disk, cacheing it all into RAM would, I expect, still take approximately the same 4GB, thus leaving me 12GB RAM (plus, in an emergency, the swap space) to run the software.  The speed with which executables could be accessed would still be good - unless I am missing something significant.

---

