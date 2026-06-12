---
title: "need help cant install anything."
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by BigCityCat on 2009-08-13
I narrowed the problem. There is a package installed. When i tried to load another program it asked me to remove this package.

this is the package.

libgpod4-nogtk

When i try and uninstall it it says.


> Cannot get the exclusive lock on the packaging backend.
Please close any other legacy packaging tools that may be open

I have nothing else open that i know of.

I already restarted with a clean session.

---

### Post by BigCityCat on 2009-08-13
more

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 168, in wrapper func(*args, **kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1231, in doInstallPackages if not self._commit_changes(): return False File "/usr/lib/packagekit/aptDBUSBackend.py", line 1704, in _commit_changes PackageKitInstallProgress(self, install_range)) File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 274, in commit res = self._fetchArchives(fetcher, pm) File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 201, in _fetchArchives if not pm.GetArchives(fetcher, self._list, self._records): SystemError: E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch)

---

### Post by starcraft.man on 2009-08-13
Easy solution, boot up in recovery console option at boot instead of normal operation. Then try uninstalling, recovery console loads almost nothing. Just uninstall as normal like: 

```
sudo apt-get remove libgpod4-nogtk
```

When your done, just start up the display manager with the following (gdm for gnome, kdm for KDE)

```
sudo /etc/init.d/gdm start
```

The package in question seems to be for ipod use, must have been installed with a music app like banshee. Don't know why it would cause trouble. If any problems reply back.

---

### Post by BigCityCat on 2009-08-13
> **starcraft.man said:**
> Easy solution, boot up in recovery console option at boot instead of normal operation. Then try uninstalling, recovery console loads almost nothing. Just uninstall as normal like: 

```
sudo apt-get remove libgpod4-nogtk
```

When your done, just start up the display manager with the following (gdm for gnome, kdm for KDE)

```
sudo /etc/init.d/gdm start
```

The package in question seems to be for ipod use, must have been installed with a music app like banshee. Don't know why it would cause trouble. If any problems reply back.

ok cool but i also have this. Is there anything else I should do?

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-3.0: Depends: firefox-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) but it is not going to be installed or
                        abrowser-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a

thanks

---

### Post by BigCityCat on 2009-08-13
Thanks for your help. Great community.

---

