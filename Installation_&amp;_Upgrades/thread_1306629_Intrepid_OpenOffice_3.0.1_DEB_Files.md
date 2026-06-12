---
title: "Intrepid OpenOffice 3.0.1 DEB Files"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2009-10-30
Hello,

  If you are using Intrepid Ibex and have OpenOffice 3.0.1 installed from the PPA Repositories, I'd like to get a copy of the deb install files.  They would be stored in:

```
/var/cache/apt/archives
```

directory on your machine.  If you have them, please post back and I'll give you a link to upload them.

Thanks,
CH

:(

---

### Post by frogotronic on 2009-11-02
Or...

you could regenerate them using the following:

Open a terminal and paste the following into it:

Code:
```

$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`

```
(the last command will take some time)

Now if you scroll to your home folder, you should find a folder called "dpkg-repack" which should have all the deb files of all your installed packages.

Taken from this post: [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

