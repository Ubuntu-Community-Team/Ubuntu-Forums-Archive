---
title: "Yum failure"
date: 2008-07-23
forum: General Help
---

### Post by Imap on 2008-07-23
Hello, 

I have posted this on x86_64 group and have not heard from anyone
and hence reposting:

Following the instructions at:
[http://www.virtuatopia.com/index.php...ng_yum_and_rpm](http://www.virtuatopia.com/index.php...ng_yum_and_rpm)
I am trying to setup centOS as domainU on my Ubuntu hardy desktop
(which is domain0). When I try the yum command I get error:

$yum --installroot=/xen/vm2/root -y groupinstall Base
Setting up Group Process
Setting up repositories
base 100% |=========================| 1.1 kB 00:00
updates 100% |=========================| 951 B 00:00
addons 100% |=========================| 951 B 00:00
extras 100% |=========================| 1.1 kB 00:00
comps.xml 100% |=========================| 914 kB 00:04
Traceback (most recent call last):
File "/usr/bin/yum", line 27, in <module>
yummain.main(sys.argv[1:])
File "/usr/share/yum-cli/yummain.py", line 92, in main
result, resultmsgs = do()
File "/usr/share/yum-cli/cli.py", line 555, in doCommands
self.doGroupSetup()
File "/var/lib/python-support/python2.5/yum/__init__.py", line 325, in doGroupSetup
self.groupInfo.add(groupfile)
File "/var/lib/python-support/python2.5/yum/Errors.py", line 55, in __init__
YumBaseError.__init__(self)
File "/var/lib/python-support/python2.5/yum/Errors.py", line 25, in __init__
self.args = args
TypeError: 'NoneType' object is not iterable

I am not familiar with python and wondering if you have any suggestions
on what could be the reason for above error.

Thanks

---

### Post by apswartz on 2008-07-23
Wow. Maybe you would get more help at a CentOS forum since they probably have more experience with yum.

---

