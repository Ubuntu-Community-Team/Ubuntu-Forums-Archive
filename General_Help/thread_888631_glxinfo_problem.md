---
title: "glxinfo problem"
date: 2008-08-13
forum: General Help
---

### Post by cmjesz on 2008-08-13
So I just installed Kubuntu with KDE 4 and also posted this on the Kubuntu forums but I figured posting it here would help too and I'm trying to install WOW following this tutorial:

[https://help.ubuntu.com/community/WorldofWarcraft#Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft#Troubleshooting)

When I run the first command I get the error below it:

$ glxinfo | grep rendering
Error: unable to open display

I have already tried running 

sudo apt-get install mesa-utils

and

sudo apt-get install nvidia-glx

but neither has helped. Any advice, I'm pretty new to Linux.

---

### Post by cmjesz on 2008-08-13
Also getting an error now trying to install/remove any package:

```

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libroken18-heimdal liboop4 libhx509-1-heimdal libasn1-8-heimdal
  libkrb5-22-heimdal
The following packages will be REMOVED:
  libasn1-8-heimdal libhx509-1-heimdal libkrb5-22-heimdal liboop4
  libroken18-heimdal nvidia-glx-new
0 upgraded, 0 newly installed, 6 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 30.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 86380 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Removing libkrb5-22-heimdal ...
Removing libhx509-1-heimdal ...
Removing libasn1-8-heimdal ...
Removing liboop4 ...
Removing libroken18-heimdal ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by cmjesz on 2008-08-13
Also tried an sudo apt-get -f install and still got the error code (1). Can anyone help?

---

