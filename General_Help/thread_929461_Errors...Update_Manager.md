---
title: "Errors...Update Manager"
date: 2008-09-25
forum: General Help
---

### Post by sashikumaran on 2008-09-25
What should I do when receiving this kind of errors or messages...

"Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 88.191.250.18 80]
Some index files failed to download, they have been ignored, or old ones used instead."

whenever run "Update Manager". I'm using Ubuntu 8.04.

---

### Post by kostkon on 2008-09-25
> **sashikumaran said:**
> What should I do when receiving this kind of errors or messages...

"Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 88.191.250.18 80]
Some index files failed to download, they have been ignored, or old ones used instead."

whenever run "Update Manager". I'm using Ubuntu 8.04.
You are trying to use repositories that are for older versions of *Ubuntu*. But it seems that these repos are down, anyway.

Thus, you should better just disable or better remove them. Go to *System -> Administration -> Software Sources* and you will find these repos in the *Third Party Software* tab. Remove them from there.

---

### Post by kostkon on 2008-09-25
*Ubuntu* 8.04 is using *Compiz Fusion* so you don't need the *Beryl* repo. *AWN* is in the official *Ubuntu* repositories, thus you also don't need this *AWN* repo you are trying to use.

But, if you want to use the latest and greatest of *AWN* then you can use this PPA (it offers the testing versions, so beware, it may be unstable):
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

The *Launchpad* page of this repo is [here]("https://launchpad.net/~awn-testing").

---

