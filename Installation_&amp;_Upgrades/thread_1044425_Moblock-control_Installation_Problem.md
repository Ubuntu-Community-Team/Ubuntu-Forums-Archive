---
title: "Moblock-control Installation Problem"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by chall32 on 2009-01-19
Hello,

My moblock-control installation is giving me problems. I've tried re-installing and am getting the following:

```
chris@dl-box:~$ sudo apt-get install --reinstall moblock-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-core libqt4-gui
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/84.8kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 205614 files and directories currently installed.)
Preparing to replace moblock-control 1.2-1+hardy (using .../moblock-control_1.2-1+hardy_i386.deb) ...
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
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
dpkg: warning - old pre-removal script returned error exit status 5
dpkg - trying script from the new package instead ...
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
/etc/init.d/moblock: 131: cannot create /etc/default/: Is a directory
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
dpkg: error processing /var/cache/apt/archives/moblock-control_1.2-1+hardy_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-control_1.2-1+hardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
chris@dl-box:~$ 

```
Any ideas or suggestions to fix would be gratefully received!

---

### Post by jre on 2009-01-21
Don't know (yet), why this happens.
But try a clean reinstall:
```
sudo aptitude purge moblock-control
sudo aptitude install moblock-control
```

---

### Post by DevilInPgh on 2009-01-27
I have the same problem as this guy, and I cannot uninstall, let alone purge, moblock-control.  Are you sure there's no problem with the package?

---

### Post by jre on 2009-01-28
**Step 1: your current situation:**
I guess you updated from a previous installation!?
Were you asked, if you want to keep any configuration file? What did you answer (for which file)?

Please give me (the output of):
```
sudo moblock-control show_config
dpkg -l moblock-control lsb-base
ls -dl /etc/default/
ls -l /etc/default/moblock
```
Your distribution (e.g. Ubuntu Hardy)
Is your aptitude/whatever output exactly the same as the already mentioned? If not, please post it. Even the smallest difference might be important.

**Step 2: Reinstall**
You may remove /etc/init.d/moblock in order to uninstall:
```
sudo rm /etc/init.d/moblock
sudo aptitude purge moblock-control
sudo aptitude install moblock-control
```

---

### Post by DevilInPgh on 2009-01-31
Output of the commands you requested:

```
jdsbluedevl@joshua:~/Desktop$ sudo moblock-control show_config
[sudo] password for jdsbluedevl: 
Creating missing /etc/default//usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
/usr/bin/moblock-control: 114: cannot create /etc/default/: Is a directory
.
 * Error 7: Missing file /etc//blocklists.list.
 * Check the BLOCKLISTS_LIST setting.
 * BLOCKLISTS_LIST is set in /etc/moblock/moblock.conf.
jdsbluedevl@joshua:~/Desktop$ dpkg -l moblock-control lsb-base
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  lsb-base       3.2-14ubuntu2  Linux Standard Base 3.2 init script function
ii  moblock-contro 1.2-1+hardy    Manage MoBlock
jdsbluedevl@joshua:~/Desktop$ ls -dl /etc/default
drwxr-xr-x 3 root root 4096 2009-01-30 23:13 /etc/default
jdsbluedevl@joshua:~/Desktop$ ls -l /etc/default/moblock
-rw-r--r-- 1 root root 324 2009-01-21 00:33 /etc/default/moblock
```

Distribution is Intrepid.

Also, using your directions, moblock-control was successfully uninstalled.

---

### Post by jre on 2009-02-01
I still don't know what exactly goes wrong...
Anyway, to fix it I think it will be enough to edit /etc/moblock/moblock.conf.
Just uncomment (remove the "#") the following lines in that file:
```
NAME="moblock"
DAEMON="/usr/bin/$NAME"
DESC="MoBlock"
```

For the next release, I have renamed moblock-control to blockcontrol, and made some internal changes, including those filenames. I guess those problems will be gone then.

---

