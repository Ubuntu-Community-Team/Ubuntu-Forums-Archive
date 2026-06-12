---
title: "Problem reinstalling python2.6"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by kingtide on 2009-09-06
I currently have python 2.5, 2.6 and 3.1 installed on my system. I previously linked /usr/bin/python to /usr/bin/python3.1, I was having some troubles with this so I attempted to link /usr/bin/python back to /usr/bin/python2.6 - accept I accidentally did the opposite (/usr/bin/python2.6 points to /usr/bin/python, not the other way around which is what I meant to do).

Now whenever I type "python -V", "python2.6 -V" or "python3.1 -V" the output is always "Python 3.1".

I attempted to fix this by reinstalling python2.6 with "sudo apt-get install --reinstall python2.6", however it fails...

```

josh@josh-laptop:~$ sudo apt-get install --reinstall python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 50 not upgraded.
4 not fully installed or removed.
Need to get 0B/10.4kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
nvidia-common failed to preconfigure, with exit status 1
(Reading database ... 165719 files and directories currently installed.)
Preparing to replace nvidia-common 0.2.11 (using .../nvidia-common_0.2.11_i386.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm pretty new to Linux so I would be very greatful for any help.

---

### Post by kingtide on 2009-09-09
Can anyone at least tell me what the error means? Please? To me it looks like it doesn't like the comma, but I don't understand how so many packages could have the same thing wrong...

---

### Post by oldfred on 2009-09-09
You are using python to run the install scripts. Since you are linked to python 3 and the scripts are still based on python 2.6? ( or maybe 2.5), the syntax is just enough different to cause error messages.
You need to undo the link so that the default is python 2.6.

---

### Post by kingtide on 2009-09-18
Thanks for the help so far :KS.

Sorry for the late reply.. I've been away from this computer for a while.

Okay so I've removed the symbolic link and I've managed to get python2.6 working (I think - "python2.6 -V" outputs as "Python2.6.2") but I'm still getting an error.

```

josh@josh-laptop:~$ sudo apt-get install --reinstall python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 81 not upgraded.
41 not fully installed or removed.
Need to get 0B/10.4kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
nvidia-common failed to preconfigure, with exit status 1
(Reading database ... 170930 files and directories currently installed.)
Preparing to replace nvidia-common 0.2.11 (using .../nvidia-common_0.2.11_i386.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

And python2.6 is my system default now. I've tried reinstalling nvidia-common but it doesn't work.

```

josh@josh-laptop:~$ sudo apt-get install --reinstall nvidia-common
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 81 not upgraded.
41 not fully installed or removed.
Need to get 0B/10.4kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
nvidia-common failed to preconfigure, with exit status 1
(Reading database ... 170930 files and directories currently installed.)
Preparing to replace nvidia-common 0.2.11 (using .../nvidia-common_0.2.11_i386.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
josh@josh-laptop:~$ python2.6
Python 2.6.2 (r262:71600, Sep  9 2009, 17:56:46) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()
josh@josh-laptop:~$ python -V
Python 2.6.2
josh@josh-laptop:~$ sudo apt-get install --reinstall python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 81 not upgraded.
41 not fully installed or removed.
Need to get 0B/10.4kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
nvidia-common failed to preconfigure, with exit status 1
(Reading database ... 170930 files and directories currently installed.)
Preparing to replace nvidia-common 0.2.11 (using .../nvidia-common_0.2.11_i386.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/bin/nvidia-detector", line 9
    except NoDatadirError, e:
                         ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-common_0.2.11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Thanks to any help.

---

