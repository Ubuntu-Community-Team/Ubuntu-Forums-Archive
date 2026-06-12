---
title: "Jaunty Compiz upgade woes (AMD 64/ GIT)"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by merville on 2009-04-29
Hi everyone,

I have just updated to Jaunty and as my Compiz GIT install is hopelessly out of date decided to remove it  and run with the Compiz packages that come with Ubuntu 9.04.

After permanent deleting Compiz and reinstalling via Synaptic, I cannot change any of my Compiz settings via Compiz Config Settings Manager. While the main window will appear, Preferences doesn't work and the plugins themselves have no content on their page.

Output from terminal when opening preferences in ccsm:

```

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Pages.py", line 1311, in ShowPreferences
    preferencesPage = PreferencesPage(self.Context)
  File "/usr/lib/python2.6/dist-packages/ccm/Pages.py", line 1160, in __init__
    self.PluginListPage = PluginListPage(context)
  File "/usr/lib/python2.6/dist-packages/ccm/Pages.py", line 1007, in __init__
    self.UpdateEnabledPluginsList()
  File "/usr/lib/python2.6/dist-packages/ccm/Pages.py", line 1048, in UpdateEnabledPluginsList
    activePlugins = self.Context.Plugins['core'].Display['active_plugins'].Value
KeyError: 'core'

```

Error when running fusion-icon:

```

 * Detected Session: gnome
 * Searching for installed applications...
Backend     : gconf
Integration : true
Profile     : default
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'


```

Output of dpkg -l | grep compiz:

```


ii  compiz                                     1:0.8.2-0ubuntu8                                           OpenGL window and compositing manager
ii  compiz-core                                1:0.8.2-0ubuntu8                                           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.8.2-0ubuntu1                                             Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.8.2-0ubuntu2                                             Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unsupported          0.7.8-0ubuntu1                                             Compiz Fusion plugins - "unsupported" collec
ii  compiz-gnome                               1:0.8.2-0ubuntu8                                           OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.8.2-0ubuntu8                                           OpenGL window and compositing manager - plug
ii  compiz-wrapper                             1:0.8.2-0ubuntu8                                           OpenGL window and compositing manager, wrapp
ii  compizconfig-backend-gconf                 0.8.2-0ubuntu1                                             Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager              0.8.2-0ubuntu1                                             Compiz configuration settings manager
rc  emerald                                    0.7.2-0ubuntu2                                             Decorator for compiz-fusion
ii  libcompizconfig0                           0.8.2-0ubuntu1                                             Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.8.2-0ubuntu1                                             Compiz configuration system bindings



```


I'd really appreciate some help as I don't want to re-install Jaunty from scratch ;-)

Thanks in advance.

---

### Post by merville on 2009-04-30
Having looked at this, I have decided to flatten the machine and re-install. This has cured it - its a pity though ;-)

---

### Post by crunchfighter on 2009-04-30
Simple solution here: [http://ubuntuforums.org/showthread.php?p=7183205#post7183205](http://ubuntuforums.org/showthread.php?p=7183205#post7183205)

---

