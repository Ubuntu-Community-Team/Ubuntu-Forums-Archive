---
title: "GCompris broken in Jaunty - workaround: install python-numeric"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by taygan on 2009-04-26
The GCompris in the Jaunty repositories doesn't work.  It's an old version with an unsatisfied dependency.  Installing python-numeric will fix it.```
sudo apt-get install python-numeric
``` The newer versions of GCompris don't need python-numeric, so hopefully they'll get the repostiories updated.

[https://bugs.launchpad.net/ubuntu/+source/gcompris/+bug/328917](https://bugs.launchpad.net/ubuntu/+source/gcompris/+bug/328917)

When I started GCompris in the terminal without python-numeric I got this:
```
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:10561): WARNING **: Binary relocation disabled
package_data_dir = /usr/share/gcompris/boards
package_locale_dir = /usr/share/locale
package_plugin_dir = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/taygan/.config/gcompris'
   Users dir '/home/taygan/My GCompris'
   Database '/home/taygan/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted
```

---

### Post by gforster on 2009-05-28
Thank you!

---

### Post by gaiterin on 2009-06-10
Thanks very much taygan!!!! :D

---

### Post by BatPenguin on 2009-07-13
> **taygan said:**
> The GCompris in the Jaunty repositories doesn't work.  It's an old version with an unsatisfied dependency.  Installing python-numeric will fix it.```
sudo apt-get install python-numeric
``` The newer versions of GCompris don't need python-numeric, so hopefully they'll get the repostiories updated.

[https://bugs.launchpad.net/ubuntu/+source/gcompris/+bug/328917](https://bugs.launchpad.net/ubuntu/+source/gcompris/+bug/328917)

When I started GCompris in the terminal without python-numeric I got this:
```
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:10561): WARNING **: Binary relocation disabled
package_data_dir = /usr/share/gcompris/boards
package_locale_dir = /usr/share/locale
package_plugin_dir = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/taygan/.config/gcompris'
   Users dir '/home/taygan/My GCompris'
   Database '/home/taygan/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted
```

Thanks! Exact same error and your fix did it. Strange how Gcompris made it to the repositories without this set as a dependancy...I thought all packages are actually tested before release. Anyway, thanks a lot!

---

