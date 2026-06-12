---
title: "Problems configuring packages - &quot;Stale NFS file handle&quot;"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by Mr Roboto on 2009-07-14
I have a number of packages that have installed but cannot be configured properly.  The two that currently do this are:

```
Setting up gnome-applets-data (2.26.1-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 364, in <module>
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 145, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 136, in install_modules_func
    os.symlink(fullpath,destpath)
OSError: [Errno 116] Stale NFS file handle
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 1

```
and
```
Setting up python-gobject (2.16.1-1ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 364, in <module>
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 145, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 136, in install_modules_func
    os.symlink(fullpath,destpath)
OSError: [Errno 116] Stale NFS file handle
dpkg: error processing python-gobject (--configure):
 subprocess post-installation script returned error exit status 1

```

I am not using NFS in any capacity (ie not as a client or server).  I have searched and searched and I cannot work out what to do to solve this.  Does anyone have any great ideas?

---

