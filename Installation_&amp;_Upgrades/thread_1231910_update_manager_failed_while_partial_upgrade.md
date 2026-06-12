---
title: "update manager failed while partial upgrade"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by sumitupadhyay on 2009-08-05
Hi ,

I upgrade from 8.04 to 8.10 through 8.10 alternate iso image.
than 8.10 to 9.04 though 9.04 alternate iso image.
now after this i run update manager to download latest updates.
Update manager suggested me for partial upgrade.
It downloads the packages, than suddenly disappeared.
I tried to run it again it does the same.
than i tried to run update-manager through terminal and i saw some failure messages.
Here is the log from terminal.

----------------------LOG-----------------------------------------------------------------------
sumit@sumit-laptop:~$ sudo update-manager 
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 100, in <module>
    controler.doPartialUpgrade()

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 1595, in doPartialUpgrade
    if not self.doDistUpgrade():

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 972, in doDistUpgrade
    self.quirks.run("StartUpgrade")

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeQuirks.py", line 77, in run
    for plugin in self.plugin_manager.get_plugins(condition):

  File "/usr/lib/python2.6/dist-packages/computerjanitor/plugin.py", line 167, in get_plugins
    filenames = self.get_plugin_files()

  File "/usr/lib/python2.6/dist-packages/computerjanitor/plugin.py", line 120, in get_plugin_files
    basenames = [x for x in os.listdir(dirname)

OSError: [Errno 2] No such file or directory: './plugins'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
none
sumit@sumit-laptop:~$ 
--------------------------------------------------------------------------------------------------

Hope to get some help.
thanks in advance.

Sumit

---

### Post by pastalavista on 2009-08-05
Try running in terminal ```
sudo aptitude safe-upgrade
```

If that doesn't help, boot in rovery mode and select "Repair Broken Packages"

If it doesn't work, let us know.

---

### Post by sumitupadhyay on 2009-08-07
Hey thanks a lot , sudo aptitude safe-upgrade  it worked for me.
Sumit

---

