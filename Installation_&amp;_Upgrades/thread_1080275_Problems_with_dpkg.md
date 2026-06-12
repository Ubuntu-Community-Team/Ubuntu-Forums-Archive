---
title: "Problems with dpkg"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by V_jeroen on 2009-02-25
Hello ,

At the moment my Ubuntu 8.10 system produces a lot of errors because of one package called totem-plugins. I want to reinstall this package but I always get an error:  ```
totem-plugins: Package is in a very bad inconsistent state - you should
```

When I do sudo apt-get install -f or apt-get remove -f I get following error : ```
 The following packages will be upgraded:
  totem-plugins
1 upgraded, 0 newly installed, 0 to remove and 305 not upgraded.
1 not fully installed or removed.
Need to get 0B/335kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166709 files and directories currently installed.)
Preparing to replace totem-plugins 2.24.2-0ubuntu4 (using .../totem-plugins_2.24.3-0ubuntu1_i386.deb) ...
/var/lib/dpkg/info/totem-plugins.prerm: 6: update-python-modules: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: Permission denied
dpkg: error processing /var/cache/apt/archives/totem-plugins_2.24.3-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/totem-plugins.postinst: 6: update-python-modules: Permission denied
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/totem-plugins_2.24.3-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The strange thing is that since I got this message my compiz effect manager does not work and also my add/remove programs is not working ! 
For example with the launch of Add/remove programs I get the following error: 
```
Failed to execute child process "/usr/bin/gnome-app-install" (Permission denied)
```

I think something is wrong with my permissions etc...

Can somebody help me with this issue ?

---

