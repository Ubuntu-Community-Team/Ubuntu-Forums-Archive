---
title: "uprade doesn`t work"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by calin_ionut on 2009-05-14
I have a problem when trying to upgrade my system. What i did before is this:

```

sudo update-alternatives --install /usr/bin/python  python /usr/bin/python2.5  10
	sudo update-alternatives --install /usr/bin/python  python /usr/bin/python2.6 1
	sudo update-alternatives --config python

```

to use the python2.5 for cedega, because it doesn`t support python2.6

Now when i trying to upgrade the system:

```

(Reading database ... 143937 files and directories currently installed.)
Preparing to replace apturl 0.3.3ubuntu1 (using .../apturl_0.3.3ubuntu1.1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1638, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1638, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing /var/cache/apt/archives/apturl_0.3.3ubuntu1.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1472, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apturl_0.3.3ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don`t get it...in /usr/share/python/debian_defaults

```

# the default python version
default-version = python2.6

# all supported python versions
supported-versions = python2.5, python2.6

# formerly supported python versions
old-versions = python2.3, python2.4

# unsupported versions, including older versions
unsupported-versions = python2.3, python2.4


```

the default version is set to 2.6


So what could be the problem?

---

### Post by calin_ionut on 2009-05-15
up

---

### Post by calin_ionut on 2009-05-16
Anyone have no idea how to fix it? I can`t even install any program because of this error ](*,)

---

### Post by calin_ionut on 2009-05-16
I fix it. :popcorn:

```

sudo rm /usr/bin/python && sudo ln -s python2.6 /usr/bin/python

```

---

