---
title: "Problem with shared c++ library on Live CD"
date: 2008-09-24
forum: General Help
---

### Post by asleeds on 2008-09-24
I am running the Desktop CD Ubuntu 8.04.1 LTS (Hardy Heron).

When trying to execute a C++ program, I get the message "error while loading shared libraries: libstdc++.so.5: cannot open shared object file: no such file or directory"

I'd welcome any suggestions for how to get this solved (preferably sticking with the Live CD for now).

Many thanks in advance, Andrew.

---

### Post by pedro_orange on 2008-09-24
sudo apt-get install libstdc++5?

---

### Post by asleeds on 2008-09-24
Thanks for the suggestion, but I get "E: couldn't find package libstdc++5"

I'm guessing it's not part of the Live CD release, right?

If I get it (from where?) can I do anything with it without installing Ubuntu 'properly'?

Thanks again, Andrew.

---

### Post by pedro_orange on 2008-09-24
Try doing a

```
apt-cache search libstdc++5
```

Perhaps cause you don't have Ubuntu installed, installing such a package isn't possible since you're running it from a LiveCD.

If you looked in /etc/apt/sources.list - what do you see?

Presumably you'd see nothing. I'm not sure. 

I think you'd find it much easier to run these applications if you had properly installed Ubuntu. However, you may need to re-compile them depending on what libraries you compiled the originals against. 
I know the package build-essential is on the LiveCD. You could try doing a:

```
sudo apt-get install build-essential
```

But I'm not sure it would actually install. 

Incidentally, what have they been compiled to? .o, .exe?

---

