---
title: "nautilus will not run, broken gvfs package cannot fix"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by DeadlyChicken on 2009-04-16
Hi,
I am fairly new to ubuntu, and I was playing about and installed WINE and steam to se ehow it would run counter strike.

Anyhow it seemed to be going great, I joined a game but then it crashed completely locking everything up.  I tried ctrl alt del and clicking and left it for about half an hour and nothing.  So I held my power button and powered off.

on reboot evreythig came up but I got this error message

Could not display "x-nautilus-desktop:///"  
Error: DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gtk.vfs.Daemon was not provided by any .service files Please select another viewer and try again.

ok I notice that I have a bunch of foolders on my desktop now like Music, Public,Pictures etc.  So I try to open my computre form the places menu and get a similar error.  So I go to try and open add remove and get another error

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f

I tried what it suggested but it fails to install gvfs

Preparing to replace gvfs 1.0.2-0ubuntu2 (using .../gvfs_1.0.2-0ubuntu3_i386.deb) ...
Unpacking replacement gvfs ...
dpkg: error processing /var/cache/apt/archives/gvfs_1.0.2-0ubuntu3_i386.deb (--unpack):
 unable to stat `./usr/share/dbus-1/services/gvfs-daemon.service' (which I was about to install): Stale NFS file handle
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gvfs_1.0.2-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

running the updates manager installs everything else but gvfs and lists it as a broken package.
Trying to reinstall it will always try to upgrade it first and fails and so ignores the reinstall.

I though about removing the package and reinstalling it, but it says its going to also remove ubuntu-desktop sao I wsant sure that was a good idea.

running ubuntu 8.10 

can anyone help ?

thanks

DC

---

