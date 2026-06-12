---
title: "system-config-samba install issues"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by chr0me on 2009-07-14
I just tried to install system-config-samba and the install crashed halfway through. Had to reboot and now can't re-install or remove the system-config-samba package.

Tried "sudo apt-get -f install" and various other things but keep getting:

matthew@matthew-ubuntu:~$ sudo apt-get -f install
[sudo] password for matthew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/582kB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package system-config-samba.
(Reading database ... 135026 files and directories currently installed.)
Preparing to replace system-config-samba 1.2.63-0ubuntu4 (using .../system-config-samba_1.2.63-0ubuntu4_all.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/system-config-samba_1.2.63-0ubuntu4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/system-config-samba_1.2.63-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Not bothered about using it but now whenever I install anything I get a message about this failed package.

---

