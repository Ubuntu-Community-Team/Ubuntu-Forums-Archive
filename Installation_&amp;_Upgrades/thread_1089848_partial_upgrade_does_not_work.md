---
title: "partial upgrade does not work"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by garble on 2009-03-07
For the last week or two, the update manager has been nagging me to do a partial upgrade because not all packages can be installed. I tried doing a partial upgrade, but right after it starts (on the "preparing upgrade" step), the window disappears. I went to the terminal and ran "sudo update-manager -d", tried the partial upgrade again, and here's the output after the window disappeared:

```
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 89, in <module>
    controler.doPartialUpgrade()

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeController.py", line 1468, in doPartialUpgrade
    if not self.doPostInitialUpdate():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeController.py", line 608, in doPostInitialUpdate
    self.quirks.run("PostInitialUpdate")

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeQuirks.py", line 66, in run
    func()

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeQuirks.py", line 135, in intrepidPostInitialUpdate
    not self._supportInModaliases("fglrx")):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeQuirks.py", line 89, in _supportInModaliases
    for filename in os.listdir(modaliasesdir):

OSError: [Errno 2] No such file or directory: './modaliases'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
```

Does anyone know how to fix this? Also, after running "sudo update-manage r -d", it says "New distribution release '9.04' is available." Should I upgrade? Will the failure of the partial upgrade affect it? Will anything bad happen if I just keep ignoring it?

---

### Post by cariboo on 2009-03-07
Never do a partial upgrade, unless you are willing to repair unmet dependencies.

I would suggest staying with your current version, until Jaunty at least goes into Beta,  there are quite a few things that could possibly break your installation.

To fix your existing problem, open a Applications-->Accessoreis-->Terminal and type:

```
sudo apt-get -f install
```

and 

```
sudo apt-get autoremove
```

The first command will install any missing dependencies if they are a available, and the second command will remove any uneeded dependencies. Then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Jim

---

### Post by garble on 2009-03-07
Thank you very much! You've been a big help.

---

### Post by jakethecake on 2009-04-10
I don't know if you waited this one out, but does creating a modaliases directory fix this issue for you? 

sudo mkdir /usr/lib/python2.5/site-packages/DistUpgrade/modaliases/
sudo update-manager --dist-upgrade

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/335416](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/335416)

---

### Post by NacIK on 2009-04-23
All I did was sudo mkdir ./plugins   Worked perfectly!!!

---

### Post by Paer86 on 2009-04-24
I have the same problem, but not sure what to do. What do you mean with "sudo mkdir ./plugins" I'm kind of new to Ubuntu and Linux.

Or should I do:
    sudo apt-get -f install 

     
     sudo apt-get autoremove 
 
     
     sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by bayvista on 2009-04-28
Many thanks for this. It solved my problem. Suggest you add a note that it involves a system rebuild and can take an hour or longer depending on your broadband.

Great work

---

