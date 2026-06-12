---
title: "apt-get autoremove error ntfs-config"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by bizarrechaos on 2009-09-12
Can anyone help me with this every time i use apt-get or synaptic to install or any thing it errors out
```
bizarrechaos@Gigatron:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 886 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ntfs-config (1.0.1-2) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ntfs-config.public is not a directory
dpkg: error processing ntfs-config (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ntfs-config
E: Sub-process /usr/bin/dpkg returned an error code (1)
bizarrechaos@Gigatron:~$ 

```

ive tried everything i know to fix it which isnt much i need some pro help
any help is greatly appreciated

---

### Post by bizarrechaos on 2009-09-14
bump

---

### Post by drs305 on 2009-09-14
Try correcting it with these commands. Run "sudo apt-get udpate" after any command which doesn't produce an error. If "update" works, don't run the rest of the commands:
```

sudo dpkg --configure -a
*if fails >*
sudo apt-get install --reinstall ntfs-config
*if fails >*
sudo apt-get purge ntfs-config

```

---

### Post by bizarrechaos on 2009-09-14
I tried what you said and it still didnt work
```
bizarrechaos@Gigatron:~$ sudo dpkg --configure -a
[sudo] password for bizarrechaos: 
Setting up ntfs-config (1.0.1-2) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ntfs-config.public is not a directory
dpkg: error processing ntfs-config (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ntfs-config
bizarrechaos@Gigatron:~$ sudo apt-get install --reinstall ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 886 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ntfs-config (1.0.1-2) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ntfs-config.public is not a directory
dpkg: error processing ntfs-config (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ntfs-config
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB


localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
bizarrechaos@Gigatron:~$ sudo apt-get purge ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.5 python2.5-minimal
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ntfs-config*
0 upgraded, 0 newly installed, 1 to remove and 886 not upgraded.
1 not fully installed or removed.
After this operation, 872kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123642 files and directories currently installed.)
Removing ntfs-config ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ntfs-config.public is not a directory
dpkg: error processing ntfs-config (--purge):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ntfs-config.public is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ntfs-config
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
bizarrechaos@Gigatron:~$ 

```

---

### Post by drs305 on 2009-09-14
Ok, would you run these commands to check the status of the ntfs-config install:
```

cat /var/lib/dpkg/status | grep -A1 "Package: ntfs-config"
cat /var/lib/dpkg/status-old | grep -A1 "Package: ntfs-config"

```

The status for a normally installed package is "install ok installed". If the first isn't normal but the second is, we can try to swap out the "status" file with it's backup. 

In this case, though, there very well may be a problem with the install, so if someone comes up with another line of attack in the meantime it very well could be a better solution.

---

### Post by bizarrechaos on 2009-09-14
BTW thanks for helping me
i checked the status of both and they are purge ok half-configured
```
bizarrechaos@Gigatron:~$ cat /var/lib/dpkg/status | grep -A1 "Package: ntfs-config"
Package: ntfs-config
Status: purge ok half-configured
bizarrechaos@Gigatron:~$ cat /var/lib/dpkg/status-old | grep -A1 "Package: ntfs-config"
Package: ntfs-config
Status: purge ok half-configured
bizarrechaos@Gigatron:~$
```

---

### Post by drs305 on 2009-09-14
> **bizarrechaos said:**
> 
Package: ntfs-config
Status: purge ok half-configured
bizarrechaos@Gigatron:~$[/code]

Ok, thanks. The following steps will probably eliminate the errors but I have to state up front that we are now going outside the APT procedures to fix the problem. 

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bad # backup
sudo gedit /var/lib/dpkg/status  # Previously backed up to status.bad

```
Remove the section from 
> Package: ntfs-config
*to* 
the empty line above next "Package:"

Save the file, then
```
sudo apt-get update
sudo apt-get upgrade
```

Once that has run, you can try to reinstall ntfs-config (if desired).

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by bizarrechaos on 2009-09-15
Thank You

---

