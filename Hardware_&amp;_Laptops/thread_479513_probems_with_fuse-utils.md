---
title: "probems with fuse-utils"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by jbowman86 on 2007-06-20
Hi all

I am trying to install fuse-utils and NTFS write support on ubuntu 6.06.1 but whenever i try to install or reinstall the fuse-utils package i get the following error...

     root@john-linux:/home/john# apt-get install fuse-utils
     Reading package lists... Done
     Building dependency tree... Done
     E: The package fuse-utils needs to be reinstalled, but I can't find an archive for it.

when i try to remove it i get the same message,

i have tried          'sudo apt-get install --reinstall fuse-utils' - same error
i have also tried         'dpkg --remove --force-remove-reinstreq fuse-utils' 
and this error message appeared

     root@john-linux:/home/john# dpkg --remove --force-remove-reinstreq fuse-utils
     dpkg - warning, overriding problem because --force enabled:
     Package is in a very bad inconsistent state - you should
     reinstall it before attempting a removal.
     (Reading database ... 81926 files and directories currently installed.)
     Removing fuse-utils ...
     /etc/init.d/fuse: line 24: /lib/init/vars.sh: No such file or directory
     invoke-rc.d: initscript fuse, action "stop" failed.
     dpkg: error processing fuse-utils (--remove):
     subprocess pre-removal script returned error exit status 1
     perl: warning: Setting locale failed. 
     perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
     perl: warning: Falling back to the standard locale ("C").
     /etc/init.d/fuse: line 24: /lib/init/vars.sh: No such file or directory
     invoke-rc.d: initscript fuse, action "start" failed.
     dpkg: error while cleaning up:
     subprocess post-installation script returned error exit status 1
     Errors were encountered while processing:
     fuse-utils

i cant make any sence from this
please can someone help as im desperate to get write support for my NTFS partitions.

---

### Post by jbowman86 on 2007-06-20
Also now when i try to use synaptic manager i get this error

     E: the package fuse-utils needs to be re-installed but i cannot find an archive for it
     E: Internal error opening cache (1). please report

---

