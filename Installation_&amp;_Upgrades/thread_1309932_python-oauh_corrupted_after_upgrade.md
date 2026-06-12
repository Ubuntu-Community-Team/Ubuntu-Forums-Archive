---
title: "python-oauh corrupted after upgrade"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by santiagozky on 2009-11-01
Hello everyone,

I just upgraded to karmic using the cdromupgrade program in the cd.
Unfourtunately during the upgrade I found a problem with the python-oauth package. I cannot upgrade, reinstall or remove it.

If I try any kind of upgrade it get this:

```
Preparing to replace python-oauth 1.0~svn1092-0ubuntu2.1~jaunty1 (using .../python-oauth_1.0a~svn1124-0ubuntu2_all.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1645, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/python-oauth_1.0a~svn1124-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/python-oauth_1.0a~svn1124-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing python-oauth (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 python-oauth
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```

So I try to reinstall:

```
 aptitude reinstall python-oauth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  python-oauth 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the python-oauth package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the python-oauth package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```

I got the deb package and try with dpkg:

```
dpkg -i python-oauth_1.0~svn1092-0ubuntu2~jaunty1_all.deb 
(Reading database ... 218508 files and directories currently installed.)
Preparing to replace python-oauth 1.0~svn1092-0ubuntu2.1~jaunty1 (using python-oauth_1.0~svn1092-0ubuntu2~jaunty1_all.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1645, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing python-oauth_1.0~svn1092-0ubuntu2~jaunty1_all.deb (--install):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-oauth_1.0~svn1092-0ubuntu2~jaunty1_all.deb
```


remove it:

```
 aptitude purge python-oauth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  python-oauth{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 123kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing python-oauth (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 python-oauth
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
```


I also deleted the apt cache and performed an update with the same results.

I'm currently out of ideas. Any suggestions for fixing this problem?

Thanks for your help

---

