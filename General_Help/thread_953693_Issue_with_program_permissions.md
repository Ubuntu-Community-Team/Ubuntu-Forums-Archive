---
title: "Issue with program permissions"
date: 2008-10-20
forum: General Help
---

### Post by Silenus on 2008-10-20
> The application "Eye of GNOME" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.[/QUOTE

This happened after I created a new /home/ partition aside from the one originally with the install. After that I corrected the .drmc or .dmrc issue that comes with it, but I am not sure how to correct this, any help would be appreciated.

> Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/eog/ui/sidebar' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/eog/ui/image_collection' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/eog/ui/sidebar' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/eog/ui/sidebar' set in a read-only source at the front of your configuration path



When I remove the toolbar option then reenable it, I get this.

> No database available to save your configuration: Unable to store a value at key '/apps/eog/ui/statusbar', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf

---

### Post by Silenus on 2008-10-20
Resolve, I used synaptic to uninstall and reinstall the application, that fixed the problem.

---

