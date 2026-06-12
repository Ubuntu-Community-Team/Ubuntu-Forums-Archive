---
title: "Broken Package won't go away"
date: 2008-11-10
forum: Hardware
---

### Post by KDB9000 on 2008-11-10
During my last update in 8.10, compiz-gnome ran into a problem and failed to update. Now it is broken and I can't fix it. Removing, reinstall, install over it, update all fails to fix the package. I can't update, install, or remove any packages with this broken package. Short of reinstalling Intrepid (I don't want to do that), nothing I have tried works.

Here is what I get:

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.7.8-0ubuntu4) but 1:0.7.8-0ubuntu4.1 is installed
                Depends: compiz-plugins (= 1:0.7.8-0ubuntu4) but 1:0.7.8-0ubuntu4.1 is installed
E: Unmet dependencies. Try using -f.

$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  compiz-gnome rhythmbox
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/3500kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package compiz-gnome.
(Reading database ... 139775 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.7.8-0ubuntu4 (using .../compiz-gnome_1%3a0.7.8-0ubuntu4.1_i386.deb) ...
Unpacking replacement compiz-gnome ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.7.8-0ubuntu4.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace rhythmbox 0.11.6svn20081008-0ubuntu4 (using .../rhythmbox_0.11.6svn20081008-0ubuntu4.1_i386.deb) ...
Unpacking replacement rhythmbox ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory
dpkg: error processing /var/cache/apt/archives/rhythmbox_0.11.6svn20081008-0ubuntu4.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.7.8-0ubuntu4.1_i386.deb
 /var/cache/apt/archives/rhythmbox_0.11.6svn20081008-0ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have checked the /usr/sbin/update-gconf-defaults file to one from a new install and there is no difference between the two. How do I fix this?

---

### Post by KDB9000 on 2008-11-10
I fixed the problem, some what. I noticed something after I posted the forum message:

The following packages have unmet dependencies:
compiz-gnome: Depends: compiz-core (= 1:0.7.8-0ubuntu4) but 1:0.7.8-0ubuntu4.1 is installed
Depends: compiz-plugins (= 1:0.7.8-0ubuntu4) but 1:0.7.8-0ubuntu4.1 is installed

In order to update compiz-gnome to 0.7.8ubuntu4.1, I need compiz-plugins 0.7.8ubuntu4, but in order to even start the compiz-gnome update I need compiz-plugins 0.7.8ubuntu4.1 install before compiz-gnome. I am not sure if there is away around this. You might be able to uninstall compiz and reinstall it with the need packages instead of updating them.

To fix the broken package, you need to go to [http://packages.ubuntu.com/intrepid](http://packages.ubuntu.com/intrepid) and find the compiz-plugins and compiz-core packages version 0.7.8ubuntu4. Once download open a terminal and go to the directory they are in and run these commands in this order:

$ sudo dpkg --install compiz-core_0.7.8-0ubuntu4_i386.deb 
$ sudo dpkg --install compiz-plugins_0.7.8-0ubuntu4_i386.deb

But all it does is fix the broken package error. I can't remove or reinstall compiz-gnome and every time I update, it still tries to update compiz-gnome even if I said not too and fails. Need a fix.

---

