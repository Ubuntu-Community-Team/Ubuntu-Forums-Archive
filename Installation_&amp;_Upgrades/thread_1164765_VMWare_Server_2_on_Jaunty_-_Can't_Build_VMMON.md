---
title: "VMWare Server 2 on Jaunty - Can't Build VMMON"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by dusten on 2009-05-20
Hi guys,

Trying to get VMWare Server 2.0 up and running. (Jaunty x86-64-bit)


After runnning the update and install scripts and going through with all default options it asks me if i'd like to build VMCI, VMMON and VMNET modules using my installed compiler (gcc)

Then when I try to start/restart the service it fails and I receive the following error:

"The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmci
vmmon
vmnet
"


Question #1) How do I CLEANLY remove these modules
#2) Should I be using a different compile program?

I've been through every forum post and thread and none of the cases are specifically like mine / don't explain how to remove and re-compile said modules.


ANY help would be greatly appreciated.

---

### Post by elmo42 on 2009-05-31
I forgot to enter a new authentication username during VMware server 2.0 installation and the similar thing happened to me. I didn't have to uninstall anything, but though this worked for me so I hope it works for you:

1. sudo gedit  /etc/vmware/hostd/authorization.xml
2. change the user (probably "root") on the <ACEDataUser> line to a different user, such as you.
3. restart the server.

Tony

---

