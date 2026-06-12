---
title: "uninstalling nero linux"
date: 2008-07-19
forum: General Help
---

### Post by StOoZ on 2008-07-19
I have installed nero-linux 3 from the nero installation , I can find it on App --> sound and video.

Now I would like to uninstall it , any idea how to do it properly?

---

### Post by brian_p on 2008-07-19
> **StOoZ said:**
> 

I have installed nero-linux 3 from the nero installation , I can find it on App --> sound and video.

Now I would like to uninstall it , any idea how to do it properly?

Assuming you got a .deb and the package name is nero-linux

```
sudo apt-get remove --purge nero-linux

```
would do it.

---

### Post by spiderbatdad on 2008-07-19
there may be an uninstaller located in the same folder as the installer...maybe in /usr/share/some_folder. You'll have to search for it. If  possible it is a good idea to install software from the repos, or deb packages, for the reason you see now. If you must compile from source, you can use "checkinstall" to attempt to create a deb, and include the new program in synaptic package manager. [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by kaibob on 2008-07-19
> **StOoZ said:**
> I have installed nero-linux 3 from the nero installation , I can find it on App --> sound and video. Now I would like to uninstall it , any idea how to do it properly?

You can remove Nero Linux 3 by way of the Synaptic Package Manager. There should be an entry for Nero in Synaptic under the category "installed (local or obsolete)." Right-click on that entry and select "mark for complete removal." Then click on the apply icon.

---

### Post by GARoss on 2009-02-16
> **kaibob said:**
> You can remove Nero Linux 3 by way of the Synaptic Package Manager. There should be an entry for Nero in Synaptic under the category "installed (local or obsolete)." Right-click on that entry and select "mark for complete removal." Then click on the apply icon.

This worked like a charm! Thanks.

---

### Post by cg_srinivas on 2010-07-06
Thanks. Its worked.

---

