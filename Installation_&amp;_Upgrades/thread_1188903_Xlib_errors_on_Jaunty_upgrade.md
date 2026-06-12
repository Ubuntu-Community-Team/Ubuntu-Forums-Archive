---
title: "Xlib errors on Jaunty upgrade"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by oygle on 2009-06-16
Ran a Jaunty upgrade from the terminal, and saw quite a few Xlib errors. After the upgrade finished (it had errors about only partial upgrade done, etc), the terminal display had ..

> 
$ gksu "sh /media/cdrom0/cdromupgrade"
gpgv: Signature made Tue 21 Apr 2009 00:02:22 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Traceback (most recent call last):
  File "/usr/share/apport/package_hook", line 58, in <module>
    pr.write(open(apport.fileutils.make_report_path(pr), 'w'))
  File "/usr/lib/python2.6/dist-packages/problem_report.py", line 306, in write
    f = open(v[0]) # file name
IOError: [Errno 21] Is a directory: '/var/log/dist-upgrade/20090615-1146'
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".


Any cause for concern ?

Oygle

---

