---
title: "Package stuck - can't remove"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by pocketchange on 2009-08-19
I had a stale PPA that I had enabled and a package was updated that just broke things.  I did a "sudo aptitude upgrade" and it upgraded autokey and the package was really bad.  Here's what happpens when I try to force removal:

```
% sudo aptitude -f remove autokey
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  autokey
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 537kB will be freed.
Writing extended state information... Done
ignored 28 file(s).
If you wish to add some of these files, please add them by name.
etckeeper warning: hardlinked files could cause problems with bzr:
./localtime
Committing to: /etc/
modified cups/subscriptions.conf
modified cups/subscriptions.conf.O
Committed revision 711.
dpkg: error processing autokey (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 autokey
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
```

I've also tried the following:

```
% sudo dpkg -r autokey
dpkg: error processing autokey (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 autokey
```

How do I get rid of this???

---

### Post by vertago1 on 2009-08-19
You probably need to use the --force-... option to dpkg to remove it if that package seems to be the only hang up.

---

### Post by Bucky Ball on 2009-08-19
As suggested in the error message, install it again either with:

```
sudo apt-get autokey
```... in a terminal or use Synaptics and then uninstall it. It can't find all of what you are asking it to uninstall. You could also try:

```
sudo apt-get autoremove
```... and see if that dislodges anything.

---

### Post by pocketchange on 2009-08-19
Okay, I did "aptitude install autokey" (couldn't do apt-get install autokey for some reason).  I then tried the following:

```
% sudo apt-get -f remove autokey
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-qscintilla2 python-xlib
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  autokey
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 537kB disk space will be freed.
Do you want to continue [Y/n]?
ignored 28 file(s).
If you wish to add some of these files, please add them by name.
etckeeper warning: hardlinked files could cause problems with bzr:
./localtime
Committing to: /etc/
modified cups/subscriptions.conf
modified cups/subscriptions.conf.O
Committed revision 714.
dpkg: error processing autokey (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 autokey
ignored 28 file(s).
If you wish to add some of these files, please add them by name.
etckeeper warning: hardlinked files could cause problems with bzr:
./localtime
Committing to: /etc/
modified cups/subscriptions.conf
modified cups/subscriptions.conf.O
Committed revision 715.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The package is 0.60.0:

```
+++-=================================-=================================-==================================================================================
iFR autokey                           0.60.0-0~jaunty                   Desktop automation utility
```

I tried downloading 0.60.2 and installing that:

```
% sudo dpkg -i autokey_0.60.2-0\~jaunty_all.deb
(Reading database ... 325141 files and directories currently installed.)
Preparing to replace autokey 0.60.0-0~jaunty (using autokey_0.60.2-0~jaunty_all.deb) ...
Traceback (most recent call last):                                                      
  File "/etc/init.d/autokey", line 16, in <module>                                      
    from autokey.interface import DOMAIN_SOCKET_PATH, PACKET_SIZE                       
  File "/usr/lib/python2.6/dist-packages/autokey/interface.py", line 638, in <module>   
    from iomediator import Key, MODIFIERS                                               
  File "/usr/lib/python2.6/dist-packages/autokey/iomediator.py", line 91, in <module>   
    from configmanager import *                                                         
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 19, in <module>
    import os, os.path, shutil, configobj, logging                                      
ImportError: No module named configobj                                                  
invoke-rc.d: initscript autokey, action "stop" failed.                                  
dpkg: warning - old pre-removal script returned error exit status 1                     
dpkg - trying script from the new package instead ...                                   
Traceback (most recent call last):                                                      
  File "/etc/init.d/autokey", line 16, in <module>                                      
    from autokey.interface import DOMAIN_SOCKET_PATH, PACKET_SIZE                       
  File "/usr/lib/python2.6/dist-packages/autokey/interface.py", line 638, in <module>   
    from iomediator import Key, MODIFIERS                                               
  File "/usr/lib/python2.6/dist-packages/autokey/iomediator.py", line 91, in <module>   
    from configmanager import *                                                         
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 19, in <module>
    import os, os.path, shutil, configobj, logging                                      
ImportError: No module named configobj                                                  
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: error processing autokey_0.60.2-0~jaunty_all.deb (--install):
 subprocess new pre-removal script returned error exit status 1
INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 16, in <module>
    from autokey.interface import DOMAIN_SOCKET_PATH, PACKET_SIZE
  File "/usr/lib/python2.6/dist-packages/autokey/interface.py", line 638, in <module>
    from iomediator import Key, MODIFIERS
  File "/usr/lib/python2.6/dist-packages/autokey/iomediator.py", line 91, in <module>
    from configmanager import *
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 19, in <module>
    import os, os.path, shutil, configobj, logging
ImportError: No module named configobj
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey_0.60.2-0~jaunty_all.deb
```

---

### Post by pocketchange on 2009-08-19
Oh, by the way, I did try the dpkg --force-all to try to remove it and that didn't work either:

```
% sudo dpkg --force-all -r autokey
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 325139 files and directories currently installed.)
Removing autokey ...
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 16, in <module>
    from autokey.interface import DOMAIN_SOCKET_PATH, PACKET_SIZE
  File "/usr/lib/python2.6/dist-packages/autokey/interface.py", line 638, in <module>
    from iomediator import Key, MODIFIERS
  File "/usr/lib/python2.6/dist-packages/autokey/iomediator.py", line 91, in <module>
    from configmanager import *
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 19, in <module>
    import os, os.path, shutil, configobj, logging
ImportError: No module named configobj
invoke-rc.d: initscript autokey, action "stop" failed.
dpkg: error processing autokey (--remove):
 subprocess pre-removal script returned error exit status 1
INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)
Traceback (most recent call last):
  File "/etc/init.d/autokey", line 16, in <module>
    from autokey.interface import DOMAIN_SOCKET_PATH, PACKET_SIZE
  File "/usr/lib/python2.6/dist-packages/autokey/interface.py", line 638, in <module>
    from iomediator import Key, MODIFIERS
  File "/usr/lib/python2.6/dist-packages/autokey/iomediator.py", line 91, in <module>
    from configmanager import *
  File "/usr/lib/python2.6/dist-packages/autokey/configmanager.py", line 19, in <module>
    import os, os.path, shutil, configobj, logging
ImportError: No module named configobj
invoke-rc.d: initscript autokey, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 autokey
```

---

### Post by Bucky Ball on 2009-08-19
Does it show up in Synaptics? Could you attempt a 'fix broken package' and then remove it once it is fixed?

---

### Post by pocketchange on 2009-08-19
I tried the fix broken package feature in synaptic, but it didn't work.  I still get all the same errors.  I've never had a package get so stuck.  Anyone know of a procedure for manually removing a package?

---

### Post by pocketchange on 2009-08-19
Ok, here's how I got past this issue:

```
% sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
% sudo vim /var/lib/dpkg/status
```

I then remove the section for autokey and save

```
sudo dpkg --configure -a
sudo aptitude upgdate
sudo aptitude upgrade
```

I can now upgrade other packages, which the error prevented me from doing before.  I realize that the package files are all still on my machine, but this at least solves some of the puzzle.

---

### Post by Bucky Ball on 2009-08-19
Nice twist. At least things are unclagged.

---

