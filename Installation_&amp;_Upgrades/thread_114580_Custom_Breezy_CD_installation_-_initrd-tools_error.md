---
title: "Custom Breezy CD installation - initrd-tools error"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by Red_Phoenix on 2006-01-08
I'm encountering a few problems while trying to come up with a 'cut down' Ubuntu install CD, and was wondering if anyone had any suggestions or solutions.

The instructions found at [https://wiki.ubuntu.com/InstallCDCustomizationHowTo](https://wiki.ubuntu.com/InstallCDCustomizationHowTo) don't seem to contain quite enough information to get everything working correctly, unfortunately.

I manage to get through to the installation phase. At around 70% of the way through the installation process, 'installing intrd-tools' terminates with an error. Looking through /var/log/* indicates that an error occurred in the 'initramfs-tools' installation process.

I suspect the apt-ftparchive step, in conjunction with the package signing process, but am not sure exactly why initramfs might die, whilst the other packages seem to be fine.

The attached script demonstrates the problem..
Requirements:
* A breezy install
* A net connection, to grab the ubuntu-keyring source
* breezy install ISO
* gpg
* qemu, to test the resulting install.
* 6 gig of free space (in /tmp by default), for a temporary qemu install file,
  the destination CD iso image, and an extracted/modified copy of the CD
* sudo password to mount the CD as a loopback device (and unmount).

Modify the BASEDIR / CDIMAGE variables in the script, as appropriate.
(NOTE: The signing passphrase is 'installtest')

On install, feel free to use a dummy IP address/config.

The script will:
* Generate a temporary gpg key for you
* Grab the ubuntu-keyring source
* Rebuild the package, signed with the temporary signing key.

The error returned will be "Unable to install initrd-tools..
An error was returned while trying to install the initrd-tools
package onto the target system."

There will be a few files to clean up in /tmp/Ubuntu once you're finished with the script.

Any help would be greatly appreciated :)

Regards,

Leigh.

---

### Post by Red_Phoenix on 2006-01-09
A few others have encountered this problem also. We're currently coordinating via email, but would appreciate any comments/suggestions - please post to the thread.

If/Once we have a solution, the wiki will be updated.

---

### Post by tjjackso on 2006-01-24
I've been beating myself up trying to remaster a Ubuntu install cd, tried both breezy and dapper flight 3, and can't seem to get it done.  I have followed the InstallCDCustomization page with out luck.  Have you made any progress?

---

### Post by Red_Phoenix on 2006-01-24
Actually yes!

One of the core problems with the previous wiki page was the apt-ftparchive command, how it was called, and what arguments were passed to it. I've updated the wiki slightly to fix this, but I'm also working on a nice easy script that does most of the work for you.

Once I have it finalised, I might add it to the wiki, but for the moment, I've included a 'pre-release' version that works nicely for me.

It allows you to:
* Specify a list of packages to retain on the CD
* Specify a custom boot splash screen

It will:
* mount the breezy ISO
* rsync the data to a temporary directory
* remove packages that aren't required
* Generate a custom gpg key for package signing.
* rebuild the ubuntu-desktop package so that it ONLY depends on the packages that you want to retain.
* regenerate the Packages/Release files required for normal installation
* generate a preseed file that facilitates installation of your packages (ubuntu-minimal, and ubuntu-desktop)
* allows you to throw in 'extra' packages into an 'extras' dir on the CD.

Notes:
* The easiest way to generate the 'package list' is to install a default ubuntu build, then use synaptic to remove packages you don't require, and copy the output of 'dpkg -l' to your $SOURCEDIR/PackageList (see script)

This script has allowed me to come up with an (approximately) 320mb CD that installs all the essential bits, most desktop bits, openssh, apache/php, mysql and a few other bits & pieces - which leaves me plenty of room to throw on the extra packages I need.

Script included below.. hopefully it won't be mangled by the board. :)

Let me know how it goes, or if you have any modifications.

---

### Post by tjjackso on 2006-01-24
Thanks for that script,  the indices part seemed to be the secret to getting things working.  I now have a dapper flight 3 build with a preseed that partitions the way I want, with a signed Release, next I'll try to start adding some things into an extras directory. :D 

[QUOTE=Red_Phoenix]Actually yes!

One of the core problems with the previous wiki page was the apt-ftparchive command, how it was called, and what arguments were passed to it. I've updated the wiki slightly to fix this, but I'm also working on a nice easy script that does most of the work for you.

Once I have it finalised, I might add it to the wiki, but for the moment, I've included a 'pre-release' version that works nicely for me.

It allows you to:
* Specify a list of packages to retain on the CD
* Specify a custom boot splash screen

It will:
* mount the breezy ISO
* rsync the data to a temporary directory
* remove packages that aren't required
* Generate a custom gpg key for package signing.
* rebuild the ubuntu-desktop package so that it ONLY depends on the packages that you want to retain.
* regenerate the Packages/Release files required for normal installation
* generate a preseed file that facilitates installation of your packages (ubuntu-minimal, and ubuntu-desktop)
* allows you to throw in 'extra' packages into an 'extras' dir on the CD.

Notes:
* The easiest way to generate the 'package list' is to install a default ubuntu build, then use synaptic to remove packages you don't require, and copy the output of 'dpkg -l' to your $SOURCEDIR/PackageList (see script)

This script has allowed me to come up with an (approximately) 320mb CD that installs all the essential bits, most desktop bits, openssh, apache/php, mysql and a few other bits & pieces - which leaves me plenty of room to throw on the extra packages I need.

Script included below.. hopefully it won't be mangled by the board. :)

Let me know how it goes, or if you have any modifications.[/QUOTE]

---

