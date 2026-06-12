---
title: "[SOLVED] Install gedit plugin?"
date: 2008-07-25
forum: General Help
---

### Post by tom66 on 2008-07-25
I would like to install the advanced bookmarks plugin. I have downloaded and untar'd it into a folder. Now what?

Thanks,
Tom

---

### Post by Nepherte on 2008-07-25
[http://ubuntuforums.org/showthread.php?p=4424711](http://ubuntuforums.org/showthread.php?p=4424711)

---

### Post by tom66 on 2008-07-25
Huh! It segfaults when I try and select it.

```

thomas@neptune:~$ gedit
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/advanced-bookmarks/plugin.py", line 51, in __init__
    conf_file = file(conf_path, "wt")
IOError: [Errno 2] No such file or directory: '/home/thomas/.gnome2/gedit/plugins/advanced-bookmarks/plugin.conf'
Segmentation fault
thomas@neptune:~$ 

```

Anybody got any idea where I might find plugin.conf?

---

### Post by tom66 on 2008-07-25
Solution - create a blank file under that name.

---

