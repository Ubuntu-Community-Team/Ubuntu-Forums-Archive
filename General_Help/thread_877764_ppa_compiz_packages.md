---
title: "ppa compiz packages"
date: 2008-08-02
forum: General Help
---

### Post by ichundu on 2008-08-02
hi,

i want to install compiz fusion with this packages:

[https://launchpad.net/~compiz/+archive]("https://launchpad.net/~compiz/+archive")

i'm not really used to ubuntu installation methods and need help to make these packages work. can anyone please describe how it could be done.

thanks

---

### Post by rune0077 on 2008-08-02
You need to add the repo to your sources list. Open System > Administration > Software Sources. The click on Third-party Software and then Add.

Now add this (from the link you gave):
```
deb http://ppa.launchpad.net/compiz/ubuntu intrepid main

```

And after that, click add again, and add this:
```
deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main
```

Now close, let it update the list, and update manager should tell you there's some new updates. Run it, and Compiz should be updated.

EDIT: I'm not sure you need the last one added. I see I only have the first (for Hardy, though), so maybe try with just that first.

---

### Post by blazemore on 2008-11-26
If you're wondering, the one with deb-src is source packages. This means you can use something like apt-build to download and compile the latest PPA'd source code.

---

### Post by Izek on 2008-11-26
So instead of intrepid, do we put down **hardy main** if we use hardy?

---

