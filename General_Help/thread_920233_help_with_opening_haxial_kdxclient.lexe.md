---
title: "help with opening haxial kdxclient.lexe"
date: 2008-09-15
forum: General Help
---

### Post by ion- on 2008-09-15
I am trying to run KDXClient.lexe ([http://www.haxial.com/products/kdx/index2.html](http://www.haxial.com/products/kdx/index2.html)) using autorun, and this makes my computer think (cursor changes to a circle), but the application will not run.

I am using Ubuntu 8.04 hardy heron.

---

### Post by adult swim on 2008-09-15
it looks like this program is for windows.  windows programs will not install directly to ubuntu

---

### Post by ion- on 2008-09-15
If you go to the link above it will show you clients for windows, mac, and linux. The application I am trying to run is a .lexe file NOT a .exe file. It should be able to run in linux.

---

### Post by adult swim on 2008-09-15
i have only seen one thing about this on the internts.  the guy got the client to set up by making the KDXServer.lexe file executable.  you can do this either by navigating to it in nautilus, right clicking KDXServer.lexe select properties, click the permissions tab, and select allow this file to be executed as a program.  then close that box and double click KDXServer.lexe.
or you can go the terminal route ```
chmod a+x /path/to/KDXServer.lexe
``` and then ```
cd /path/to/file
``` followed by ```
KDXServer.lexe
```

---

### Post by ion- on 2008-09-15
Note: I am trying to run KDXClient.lexe not KDXServer.lexe

I've tried setting properties -> permissions -> allow executing file as program with no result.
I've tried executing the file as root.
I've tried setting chmod +x ~/Desktop/KDXClient.lexe; ~/Desktop/KDXClient.lexe and the result is "bash: KDXClient.lexe: command not found"

The only solution I've found for this is to download the windows version and run it through wine, but that seems like giving up to me. I guess I will email the developer (Haxial) with my question.

---

### Post by ion- on 2008-09-15
Finally figured it out.
I was missing the libstdc++5 package.
Here's a link with the dependencies:[http://packages.debian.org/unstable/base/libstdc++5](http://packages.debian.org/unstable/base/libstdc++5)

---

