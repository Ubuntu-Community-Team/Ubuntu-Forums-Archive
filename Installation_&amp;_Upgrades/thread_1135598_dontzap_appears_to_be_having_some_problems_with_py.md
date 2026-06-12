---
title: "dontzap appears to be having some problems with pycentral"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by stucky on 2009-04-24
Will file a bug report if no one has an easy fix.

Upgrade to 9.04 went fine for the most part, just a couple of easy fixes required. However, I wanted to reenable the ctrl-alt-backspace option. When I ran the command dontzap --disable per the release notes it came back and told me that dontzap wasn't installed, blah blah blah. So apt-get install dontzap and it appeared to run just fine except once installed that command appeared to do nothing and the server flag option was used in xorg. The problem is that now everytime I try and do anything with apt or dpkg I get the following squawking from the system:
```

root@mjollnir:/home/dave# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/6618B of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 232787 files and directories currently installed.)
Preparing to replace dontzap 0.1.2 (using .../archives/dontzap_0.1.2_all.deb) ...
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
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
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
dpkg: error processing /var/cache/apt/archives/dontzap_0.1.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1475, in run
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
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dontzap_0.1.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas? I have tried purging, reinstalling and talking to it nicely but same results.

Also of note, dpkg --configure -a results in this:
```

root@mjollnir:/home/dave# dpkg --configure -a
dpkg: error processing dontzap (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 dontzap

```

---

### Post by cariboo on 2009-04-24
Instead of using dontzap, although it worked for me, you can just add the following to /etc/X11/xorg.conf:

```
Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

You don't need the dontzap script, as all it does is write the above entries to /etc/X11/xorg.conf

---

### Post by stucky on 2009-04-24
> **cariboo907 said:**
> Instead of using dontzap, although it worked for me, you can just add the following to /etc/X11/xorg.conf:

```
Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

Right, that's up in the initial part of my post, although not very clearly stated. That was the only thing that worked. Unfortunately I just can't do anything with apt or dpkg now.

---

### Post by stucky on 2009-04-25
* bump *

---

