---
title: "MoBlock uninstall error"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by JarG0n on 2009-03-16
Can someone help with this MoBlock error?  I've followed every instruction I can find on these forums, and nothing will remove MoBlock from my system.  I originally put an incorrect range into /etc/moblock/allow.***, and this caused errors that could not be recovered from.

When uninstalling using Synaptic:

E: moblock-control: subprocess post-installation script returned error exit status 2

E: moblock-control: subprocess pre-removal script returned error exit status 5

Via terminal:

```

user@my-desktop:/etc/moblock$ sudo apt-get purge moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnfnetlink0 p7zip libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock* moblock-control*
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 524kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119336 files and directories currently installed.)
Removing moblock-control ...
Creating missing /etc/default//etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
.
 * /etc/init.d/moblock:  not installed.
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock-control (--purge):
 subprocess pre-removal script returned error exit status 5
Removing moblock ...
Purging configuration files for moblock ...
Processing triggers for man-db ...
Errors were encountered while processing:
 moblock-control
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@my-desktop:/etc/moblock$ 

user@my-desktop:/etc/moblock$ sudo apt-get purge moblock-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnfnetlink0 p7zip libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock-control*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 397kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119325 files and directories currently installed.)
Removing moblock-control ...
Creating missing /etc/default//etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
.
Could not detect an IPBlocker daemon. MoBlock and NFBlockD are supported.
Neither of them was found in PATH: /sbin:/bin:/usr/sbin:/usr/bin.
Error 6: You may set NAME, DAEMON and DESC manually in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock-control (--purge):
 subprocess pre-removal script returned error exit status 6
Errors were encountered while processing:
 moblock-control
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@my-desktop:/etc/moblock$ 

```

---

### Post by Partyboi2 on 2009-03-16
Open a terminal and move /etc/init.d/moblock out of the way, then try removing moblock.
```
sudo mv /etc/init.d/moblock /etc/init.d/moblock.old
```
```
sudo apt-get --purge remove moblock
```

---

### Post by JarG0n on 2009-03-16
This worked!  Thank you!  I was able to uninstall both moblock and moblock-control, subsequently reinstalling successfully.

May I ask how did you arrive at this solution?  I'm trying to learn something here, lol.  :popcorn:

---

### Post by Partyboi2 on 2009-03-16
I stumbled upon the same problem in [[COLOR=Blue]this[/COLOR]]("http://www.uluga.ubuntuforums.org/showthread.php?t=1044425") thread.

---

