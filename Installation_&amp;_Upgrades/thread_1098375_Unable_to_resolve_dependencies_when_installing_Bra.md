---
title: "Unable to resolve dependencies when installing Brasero 0.8.4"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by killpotts on 2009-03-16
Hey all, I am trying to install Braser 0.8.4 on Ubuntu 8.10 ( comes with Brasero 0.8.2 ) but have ran into a brick wall. 

I first picked up the package "Brasero_0.8.4-0ubuntu1_i386.deb" but when trying to run it I get the error: 

```

Error: Dependency is not satisfiable: ligbail-common

```

And so I set out to find "libgail-common_1.22.1-0ubuntu1_1386.deb"

which gave me:

```

Error: Dependency is not satisfiable: ligbail18

```

And so I set out to find "libgail18_1.22.1-0ubuntu_i386.deb"

which luckily didn't need any other dependencies, but has finally led me to:

```

Install Complete

Failed to install package: libgail18

```

And here I am. :(

---

### Post by killpotts on 2009-03-17
Alternatively, if anyone can help me figure out why I am getting the following error ( click link below ) in 0.8.2, it would help me all the same.

[https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/211528](https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/211528)

None of the fixes provided on that page work for me. It may have something to do with the strange fact that I cannot play the DVD I am trying to copy in Mplayer, VLC player, or the default movie player. All of them run into some kind of obscure error.

---

### Post by mc4man on 2009-03-17
Intrepid doesn't use libgail-common or liggail18 (hardy does, jaunty does
Where did you get the .deb from?

Try one from here (0.9.1 or 0.8.4
[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

Edit:
If you can't play the dvd then brasero won't do any better, may have a structure protection that libdvdread or nav can't deal with.
If you wish post the title name

---

