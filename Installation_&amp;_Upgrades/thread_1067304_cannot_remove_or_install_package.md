---
title: "cannot remove or install package"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by tjk on 2009-02-11
For months I have not been able to install or remove a package, but just yesterday apt-get will not even do any package upgrades until I fix this problem.  Here's what I get when running various commands:
----------------------------------------------------------
_**tim@x:~$ sudo apt-get upgrade**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bayonne: Depends: libccscript2-0.6-3 but it is not installable
E: Unmet dependencies. Try using -f.
_**tim@x:~$ sudo apt-get -f install**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bayonne
Suggested packages:
  bayonne-doc bayonne-prompts-en
The following packages will be upgraded:
  bayonne
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/613kB of archives.
After this operation, 905kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 438235 files and directories currently installed.)
Preparing to replace bayonne 1.2.16-6build2 (using .../bayonne_2.3.2-1build2_amd64.deb) ...
/etc/init.d/bayonne: 45: source: not found
invoke-rc.d: initscript bayonne, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/bayonne_2.3.2-1build2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/bayonne_2.3.2-1build2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
_**tim@x:~$ sudo dpkg --configure -a**_
_**tim@x:~$ sudo apt-get -f install**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bayonne
Suggested packages:
  bayonne-doc bayonne-prompts-en
The following packages will be upgraded:
  bayonne
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/613kB of archives.
After this operation, 905kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 438235 files and directories currently installed.)
Preparing to replace bayonne 1.2.16-6build2 (using .../bayonne_2.3.2-1build2_amd64.deb) ...
/etc/init.d/bayonne: 45: source: not found
invoke-rc.d: initscript bayonne, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/bayonne_2.3.2-1build2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/bayonne_2.3.2-1build2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
_**tim@x:~$ sudo apt-get dist-upgrade**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bayonne: Depends: libccscript2-0.6-3 but it is not installable
E: Unmet dependencies. Try using -f.
---------------------------------------------------------------
I would prefer to remove bayonne completely from my computer...  Please help...

---

### Post by wpshooter on 2009-02-11
Have you tried going into System/administration/software sources and making sure that all of the proper boxes are checked on the Ubuntu software tab ?

If they are then, I would go to the updates tab and mark the backports check box (if it is not marked) and the exit out of software sources and reload when you do.  Then restart the computer and after that do a check for new software with update manager and see if you get updates that need to be installed.  If you do, then install them and then go back into software sources and turn the backports check box off.

Then use Synaptic to install/uninstall software updates and forget about the archaic apt-get commands.

Good luck.

---

### Post by tjk on 2009-02-11
> **wpshooter said:**
> Have you tried going into System/administration/software sources and making sure that all of the proper boxes are checked on the Ubuntu software tab ?

If they are then, I would go to the updates tab and mark the backports check box (if it is not marked) and the exit out of software sources and reload when you do.  Then restart the computer and after that do a check for new software with update manager and see if you get updates that need to be installed.  If you do, then install them and then go back into software sources and turn the backports check box off.

Then use Synaptic to install/uninstall software updates and forget about the archaic apt-get commands.


Checked my sources file for "proper" repositories.  Looked okay.
Then did what you suggested with backports and this was the result:
----------------------------------------------------------------
started with update then:
_**tim@x:~$ sudo apt-get upgrade**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bayonne: Depends: libccscript2-0.6-3 but it is not installable
E: Unmet dependencies. Try using -f.
_**tim@x:~$ sudo apt-get -f install**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  tcltls
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bayonne
Suggested packages:
  bayonne-doc bayonne-prompts-en
The following packages will be upgraded:
  bayonne
1 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
Need to get 0B/613kB of archives.
After this operation, 905kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package bayonne.
(Reading database ... 437271 files and directories currently installed.)
Preparing to replace bayonne 1.2.16-6build2 (using .../bayonne_2.3.2-1build2_amd64.deb) ...
/etc/init.d/bayonne: 45: source: not found
invoke-rc.d: initscript bayonne, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/bayonne_2.3.2-1build2_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/bayonne_2.3.2-1build2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
_**tim@x:~$ **_
-------------------------------------------------------------------------

So... as I said earlier... I cannot upgrade any files (29) because of the bayonne problem...  any other ideas.

---

