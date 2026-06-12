---
title: "Updating Freezes, causing problems..."
date: 2008-09-13
forum: General Help
---

### Post by goldenglow21 on 2008-09-13
I've had almost no problem I could not find the answer to on these forums since I've installed Ubuntu. But last night, I ran update manager and installed 9 updates... On one of the updates it says something about...

"apt-get-something-commercial (9.3)
caching application data..."

then it freezes and does nothing. The first time this happened the update manager and synaptic would not run until I found the following line to run in terminal.

"dpkg --remove --force-remove-reinstreq webmin"

Now I can run the updates, but WINE now for some reason runs super SLOW, like 1 fps. And when I tried to reinstall wine, it freezes at the EXACT same line as the update above.

Also missing is my battery icon for some reason.
Just seems like a lot of things have messed up from that one update freezing. Any help would be greatly greatly appreciated. I would like to fix the problem without having to reinstall if at all possible.

---

### Post by Neo_The_User on 2008-09-13
try this

sudo dpkg --configure app-install-data-commercial

---

### Post by goldenglow21 on 2008-09-13
Setting up app-install-data-commercial (9.3) ...
Caching application data...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 6, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/update.py", line 104, in main
    generate_menu_cache(options.desktop_dir, options.cache_dir)
  File "/usr/lib/python2.5/site-packages/AppInstall/update.py", line 70, in generate_menu_cache
    menu.createMenuCache(cache_dir)
  File "/usr/lib/python2.5/site-packages/AppInstall/CoreMenu.py", line 40, in createMenuCache
    pickle.dump(self.pickle, open('%s/%s' % (targetdir,fname),'w'), 2)
IOError: [Errno 30] Read-only file system: '/var/cache/app-install/menu.p'

dpkg: error processing app-install-data-commercial (--configure):
 unable to flush updated status of `app-install-data-commercial': Read-only file system
dpkg: failed to open `/var/lib/dpkg/status' for writing status information: Read-only file system



thats what i got, and wine still seems to be broke running very slowly.

---

### Post by Crafty Kisses on 2008-09-13
Try the following command and see if that solves your package issue:
```
sudo dpkg --configure -a
```

---

### Post by goldenglow21 on 2008-09-13
> **Codename said:**
> Try the following command and see if that solves your package issue:
```
sudo dpkg --configure -a
```

Setting up libfreetype6 (2.3.5-1ubuntu4.8.04.1) ...

Setting up libxml2 (2.6.31.dfsg-2ubuntu1.2) ...

Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up python-gtkhtml2 (2.19.1-0ubuntu7.1) ...

Setting up app-install-data-commercial (9.3) ...
Caching application data...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 6, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/update.py", line 104, in main
    generate_menu_cache(options.desktop_dir, options.cache_dir)
  File "/usr/lib/python2.5/site-packages/AppInstall/update.py", line 70, in generate_menu_cache
    menu.createMenuCache(cache_dir)
  File "/usr/lib/python2.5/site-packages/AppInstall/CoreMenu.py", line 40, in createMenuCache
    pickle.dump(self.pickle, open('%s/%s' % (targetdir,fname),'w'), 2)
IOError: [Errno 30] Read-only file system: '/var/cache/app-install/menu.p'

dpkg: error processing app-install-data-commercial (--configure):
 unable to flush updated status of `app-install-data-commercial': Read-only file system
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted



Right when ubuntu boots after the login screen, i get a small pop-up, "the configuration defaults for GNOME power manager is not installed correctly" something like that. Not sure how to fix that and wine.

---

### Post by goldenglow21 on 2008-09-13
tried installing gnome-power-manager through synaptic but i get

"E: app-install-data-commercial: unable to flush updated status of `app-install-data-commercial'"

also, the routine drive check on bootup runs but fails, gives me some error.

---

### Post by goldenglow21 on 2008-09-14
bump, im dying here...

---

### Post by goldenglow21 on 2008-09-16
the power has been out here for the last couple of days, finally got a chance to check for any replies... nothing huh?

should I just reinstall? I hate to do that and lose everything, but is that the only option?

---

