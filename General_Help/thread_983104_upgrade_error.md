---
title: "upgrade error"
date: 2008-11-15
forum: General Help
---

### Post by moore.bryan on 2008-11-15
what the hell does this even mean:
```
Writing extended state information... Error!
E: I wasn't able to locate file for the gutsy-wallpapers package. This might mean you need to manually fix this package.
```
gutsy-wallpapers is installed already, but when i try to even remove it, i can't. so, uh, how do i even begin to get rid of this? nothing which requires gtk to run works right now, so no synaptic, firefox, etc. only cli.
help!
:-)
and i get this when i try to uninstall:
```
moore@thinkpad:~$ sudo dpkg --remove gutsy-wallpapers
dpkg: error processing gutsy-wallpapers (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gutsy-wallpapers

```

---

### Post by Steve1961 on 2008-11-15
> **moore.bryan said:**
> what the hell does this even mean:
```
Writing extended state information... Error!
E: I wasn't able to locate file for the gutsy-wallpapers package. This might mean you need to manually fix this package.
```
gutsy-wallpapers is installed already, but when i try to even remove it, i can't. so, uh, how do i even begin to get rid of this? nothing which requires gtk to run works right now, so no synaptic, firefox, etc. only cli.
help!
:-)
and i get this when i try to uninstall:
```
moore@thinkpad:~$ sudo dpkg --remove gutsy-wallpapers
dpkg: error processing gutsy-wallpapers (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gutsy-wallpapers

```

Try sudo dpkg --remove --force-remove-reinstreq gutsy-wallpapers
Then sudo dpkg --configure -a
Then sudo apt-get -f install

---

### Post by moore.bryan on 2008-11-15
thanks for the quick reply... i just get a bunch of errors:
```
moore@thinkpad:~$ sudo dpkg --remove --force-remove-reinstreq gutsy-wallpapers
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 267513 files and directories currently installed.)
Removing gutsy-wallpapers ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing gutsy-wallpapers (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gutsy-wallpapers

```

---

### Post by Steve1961 on 2008-11-15
Must be really badly broken.  You could also try sudo apt-get --reinstall install gutsy-wallpapers.  If that doesn't work though I'm afraid I'm at a loss.

---

### Post by moore.bryan on 2008-11-15
unfortunately, no dice; i just keep getting a bunch of errors. i run a server install with openbox, so the "usual" upgrade methods don't work for me... i wish ubuntu made cli dist-upgrading easier.

perhaps someone else has some insight... if not, a complete reinstall is up.

even when i download gutsy-wallpapers separately and try to install, i get errors:
```
moore@thinkpad:~/Downloads$ sudo dpkg -i gutsy-wallpapers_0.20_all.deb
Selecting previously deselected package gutsy-wallpapers.
(Reading database ... 268069 files and directories currently installed.)
Preparing to replace gutsy-wallpapers 0.19 (using gutsy-wallpapers_0.20_all.deb) ...
Unpacking replacement gutsy-wallpapers ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing gutsy-wallpapers_0.20_all.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/backgrounds/gutsy-final-ubuntu.png')
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gutsy-wallpapers_0.20_all.deb

```
wtf?

---

### Post by Steve1961 on 2008-11-15
Just done a quick search.  You could also try sudo dpkg --purge --force-all gutsy-wallpapers

Edit. Just read your last post, so doubt it will work.

---

### Post by moore.bryan on 2008-11-15
thanks for all your help, but it still won't work. i think i might just use the "nuclear option" and reinstall the whole system... it's about time for a change and fresh start.

once again, thanks for all your help.

---

