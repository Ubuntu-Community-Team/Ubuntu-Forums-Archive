---
title: "[SOLVED] Dpkg doesnt work :("
date: 2008-09-12
forum: General Help
---

### Post by marufaberlin on 2008-09-12
While installing ClamAV, my computer crashed (due to a nother application). The installation did not finish correctly.

Now when I issue
```

$ sudo dpkg --configure -a

```
I get the following output:
```

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted (core dumped)

```

What should I do???:(

---

### Post by marufaberlin on 2008-09-12
SOLVED, but thx for those who read my post anyway.

For anyone who has the same problem:

I used synaptic to try install another package and it told me (at the end of the console output) that packages were incorrecly installed. In my case they were lirc and kaptain.

This code worked for me:
```

sudo dpkg --remove lirc kaptain
sudo apt-get -f install
sudo dpkg --configure -a

```

---

