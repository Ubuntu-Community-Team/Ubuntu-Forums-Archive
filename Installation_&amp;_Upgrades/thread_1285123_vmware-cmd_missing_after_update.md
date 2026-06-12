---
title: "vmware-cmd missing after update"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by jaywhy13 on 2009-10-07
I updated to Jaunty recently and vmware updated itself. Now vmware-cmd is missing. How can I get it back?

---

### Post by ant2ne on 2009-11-06
[http://unixfoo.blogspot.com/2008/11/vmware-20-cli-management-utility.html](http://unixfoo.blogspot.com/2008/11/vmware-20-cli-management-utility.html)

> Power off a virtual machine :

[root@foo-vm12 bin]# /usr/vmware/bin/vmware-vim-cmd vmsvc/power.off 128
Powered off
[root@foo-vm12 bin]#

Power on a virtual machine :

[root@foo-vm12 bin]# /usr/vmware/bin/vmware-vim-cmd vmsvc/power.on 128
Powered on
[root@foo-vm12 bin]#

Also

You have to make sure that root has an "Administrator" role under permissions in the 
web interface.

[http://ubuntuforums.org/showthread.php?t=998271](http://ubuntuforums.org/showthread.php?t=998271)

---

