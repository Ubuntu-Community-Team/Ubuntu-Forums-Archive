---
title: "Restore Tar"
date: 2008-08-02
forum: General Help
---

### Post by sjoerdovitch on 2008-08-02
As a newbie I deleted tar in the bin folder.
How can I restore it??

It is Xubuntu 6

Thanks

---

### Post by tamoneya on 2008-08-02
take a look at this artice.  [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

It is fairly wordy but you can learn a lot from it.

---

### Post by geirha on 2008-08-02
You deleted /bin/tar? how did you mange that? :)

Anyway, figure out which package it is in, and reinstall it:
```

$ dpkg -S /bin/tar
[COLOR="Blue"]tar[/COLOR]: /bin/tar
$ sudo aptitude reinstall [COLOR="Blue"]tar[/COLOR]

```

---

### Post by coffeecat on 2008-08-02
Boot up from the live CD you used to install Xubuntu, mount your root partition and copy /bin/tar from the live environment to /bin/tar on your HD. You'll need to use 'sudo cp' because the destination folder is root-owned. You don't need a password in the live environment - just use sudo.

Do you know how to mount the root partition?

**Edit** Ignore this; **geirha**'s way is much to be preferred. :)

---

### Post by argail1980 on 2008-08-02
open synaptic (System > Administration > Synaptic)

search for tar, rightclick tar and choose "reinstall" (or similar, my menus are in German). If that does not work, first uninstall then reinstall.

---

