---
title: "CCSM won't run after git install"
date: 2008-10-27
forum: General Help
---

### Post by chaser209 on 2008-10-27
Compiz Fusion Settings Manager won't run after GIT install. Running from the terminal gives the following error message:

```

Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

I tried re-install in synaptic, and complete removal and re-install in synaptic.

When I installed from the GIT, I didn't uninstall regular compiz, not sure if that's causing the problem.

---

### Post by borlosky on 2008-11-12
that actually may be the issue, when i installed compiz from git i had to remove ALL compiz related items before installing it, i first went to add/remove, got rid of all compiz, then went to synaptic, removed everything compiz related. then installed compiz from git, and all works 100% (btw once you get compiz installed from git, i reccomend getting this plugin: [http://www.elementsplugin.com/]("http://www.elementsplugin.com/"))

::edited for spelling::

---

### Post by loomsen on 2008-11-12
[KLICK ME](http://ubuntuforums.org/showthread.php?t=971379)

---

### Post by darkgeny on 2009-03-08
try this my solution, it is temporary solution but the compiz and settings now work!

[http://darkgeny.wordpress.com/](http://darkgeny.wordpress.com/)

this is:

undefined symbol: ccsGetPluginStrExtensions AND TypeError: __init__()
8 03 2009

Running compiz, error:

SOLVED:

LIBGL_ALWAYS_INDIRECT=1 compiz &#8211;replace &#8211;ignore-desktop-hints ccp &
emerald &#8211;replace &

Running fusion-icon, error compiz:

fusion-icon &#8211;no-start

Running fusion-icon or ccsm, error:

Traceback (most recent call last):
File &#8220;/usr/local/bin/ccsm&#8221;, line 38, in
import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

SOLVED with this my solution:

cd /usr/lib/python2.6/dist-packages
sudo mv compizconfig.so compizconfig.so.2.6
sudo ln -s /usr/local/lib/python2.5/site-packages/compizconfig.so compizconfig.so

Runninc ccsm or ccsm, error:

Initializing core options&#8230;done
Traceback (most recent call last):
File &#8220;/usr/local/bin/ccsm&#8221;, line 68, in
idle = ccm.IdleSettingsParser(context)
TypeError: __init__() takes exactly 3 arguments (2 given)

SOLVED with this my solution:

sudo vim /usr/local/bin/ccsm

change first row:
#!/usr/bin/python

to new row:
#!/usr/bin/python2.5

Now all rights!

---

