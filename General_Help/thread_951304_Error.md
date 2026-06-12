---
title: "Error"
date: 2008-10-18
forum: General Help
---

### Post by Pinejoker on 2008-10-18
apt.log

Traceback (most recent call last):
  File "/usr/share/apport/package_hook", line 15, in <module>
    import apport, apport.fileutils
ImportError: No module named apport

main.log

2008-10-17 23:03:37,565 ERROR got an error from dpkg for pkg: 'driverloader': 'subprocess post-installation script returned error exit status 1
'
2008-10-17 23:03:37,597 ERROR got an error from dpkg for pkg: 'driverloader': 'subprocess post-installation script returned error exit status 1
'
2008-10-17 23:08:10,916 WARNING no activity on terminal for 240 seconds (Configuring scrollkeeper)
2008-10-17 23:20:01,226 ERROR SystemError from cache.commit(): installArchives() failed
2008-10-17 23:20:41,638 DEBUG setting MinAge to 2
2008-10-17 23:20:41,639 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'

term.log

Errors were encountered while processing:
 driverloader
Traceback (most recent call last):
  File "logging/__init__.py", line 753, in emit
  File "logging/__init__.py", line 731, in flush
IOError: [Errno 9] Bad file descriptor
    self.run_crash(f)
  File "/var/lib/python-support/python2.5/apport/ui.py", line 179, in run_crash
    self.collect_info()
  File "/var/lib/python-support/python2.5/apport/ui.py", line 348, in collect_info
    icthread.exc_raise()
  File "/var/lib/python-support/python2.5/apport/REThread.py", line 37, in run
    self._retval = self.__target(*self.__args, **self.__kwargs)
  File "/var/lib/python-support/python2.5/apport/ui.py", line 31, in thread_collect_info
    report.add_gdb_info()
  File "/var/lib/python-support/python2.5/apport/report.py", line 405, in add_gdb_info
    self['CoreDump'].write(open(core, 'w'))
  File "/var/lib/python-support/python2.5/problem_report.py", line 54, in write
    block = gz.read(1048576)
  File "/usr/lib/python2.5/gzip.py", line 227, in read
    self._read(readsize)
  File "/usr/lib/python2.5/gzip.py", line 263, in _read
    self._read_gzip_header()
  File "/usr/lib/python2.5/gzip.py", line 164, in _read_gzip_header
    raise IOError, 'Not a gzipped file'
IOError: Not a gzipped file
gutsy: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
Setting up driverloader (2.44-k2.6.24-21-generic-1.ubuntu) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.44
No pre-built modules for: Ubuntu-7.10 linux-2.6.20-17-generic i686-SMP
Please obtain the appropriate variant of this package for your system
or try the generic DEB or tar version.
dpkg: error processing driverloader (--configure):
 subprocess post-installation script returned error exit status 1


could someone help me please...

---

