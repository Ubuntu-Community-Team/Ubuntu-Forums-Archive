---
title: "Can I create a AptOnCD disc from a previously created package list?"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Linewbie on 2009-09-17
Hi, I have recently reinstalled Ubuntu, I tried to create an AptOnCD disc on my last installation, but all of the installed debs were not listed when I ran AptOnCD.
So (as a last resort), I created a list of packages using this command:
dpkg --get-selections | grep install | cut -f1 > packages.dpkg

So, now I have a list of packages on my new install, but how do I create a AptOnCd disc using this list?
----------------------------------------
The package list looks like this:
abcde
acl
.
.
.
zip
zlib1g
----------------------------------------
I know that I have to download everything, but I keep getting errors trying to download:
--------------------------------------------------------
sudo apt-get -d -m source `cat packages.dpkg`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'acpi-support' packaging is maintained in the 'Svn' version control system at:
svn://svn.debian.org/collab-maint/deb-maint/acpi-support/trunk
NOTICE: 'acpid' packaging is maintained in the 'Svn' version control system at:
[https://bollin.googlecode.com/svn/acpid/trunk](https://bollin.googlecode.com/svn/acpid/trunk)
NOTICE: 'adduser' packaging is maintained in the 'Svn' version control system at:
svn://svn.debian.org/adduser/
E: Unable to find a source package for adept-common
----------------------------------------------------
Or can I use the aptoncd and apt-get commands with a pipe with my packages list to create the .iso file?

I know that I have to download them first for AptOnCD to work, but how do I achieve this? (I am probably misusing the cat command, but there must be a way to take a package list and turn it into an iso using AptOnCD.)

Thanks!
:guitar:

---

